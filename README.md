# gsdslack
GSD Slack


Documentation:
- userLocaltime - UTC_TIMEZONE + Timezone OFfset
- edited messages - new row is added to the channelMessages table, with the same slackMessageId and a new userLocaltime
- deleted messages - the user localtime should be added to the column deletedLocaltime. This value should be added to all rows with same slackMessageId (there will be more than one if the message has been edited before)


slackUserStatuslog (some of the columns example):
userLocaltime       | userTimezoneOffset | userTimezoneLabel
2017-07-07 12:05:24 | -7                 | Pacific Daylight Time
2017-07-07 20:06:24 | 1                  | British Summer Time

This time structure allow us to analyse the contribution on local time (if they were working in between 9-5, for example) but also if people from different timezones were working at the same time.

user table:
- 20180217: new column added 'invited'. Default is 0. Used for Matthew's system to track who has already being invited to Slack.

IMPORTANT:
- Tableau analyses the RAW date, considering the DB UTC local time.
- MySQL workbench, when accesssing from the local machine it will show the machine local time! 
