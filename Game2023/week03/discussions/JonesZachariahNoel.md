# Jones Zachariah Noel

Building on top of the previous solution. And would do the usual way where the client is creating a voting it also has a field to set if it's "send now" or "send later".

Application would have a scheduler set for every 5 mins with CRON exp which would check if there is anything scheduled based on reminder/alert settings (before 15 mins or last 5 mins for voting) in DynamoDB then send out reminders/alerts which are basically subscription from the app client.

With AppSync query to get votings, they will include the scheduled time and based on which FE will render time or allow to cast votes.

Updates would bring in an admin panel where the client can create a marketing campaign contents which as topics based on users consent true or false will subscribe or unsubscribe them from the topic. To the subscribers of the topic, an email would be sent.
