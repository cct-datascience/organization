# NCSA TERRA REF Meeting - 2019-09-05

Participants: David, Julian, Chris, Max, Rob, Sean

## Gantry cache

- Sean preparing document for gantry cache server, will be ready by end of week
- [ ] Julian to review, make list of questions
- [ ] Schedule two-hour meeting next week for questions (Chris & Julian)

## IRODS Clowder plugin

- [ ] Julian to look into plugin

Discussion between Chris & Julian after meeting:

- It seems there is a basic assumption in Clowder that there will be no external/direct access by end-users to the underlying data storage.
- Reason for suspicion: There appears to be a single credential for a storage service like S3 or IRODS.
- This means that this would be a problem if we wanted to separate different users' data 'physically', i.e. different S3 account-buckets, or different IRODS accounts.

Is this suspicion accurate? Am I missing something? Is there a way in Clowder to achieve this?

Note: Posted this question on the Clowder Slack workspace in the #developers channel.