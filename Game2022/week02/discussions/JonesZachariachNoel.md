# Jones Zachariah Noel

I would continue to build on the solution from the [previous week](https://www.linkedin.com/feed/update/urn:li:activity:7015449163140116480?commentUrn=urn%3Ali%3Acomment%3A%28activity%3A7015449163140116480%2C7015578361364197376%29)

Using AppSync queries where the filter key "only_free_polls" if false will query all the polls from DynamoDB or if true, will query items which have {is_paid: false} the FE will continue to use one query and the value of "only_free_polls" would be based on the filter button.

The credits top-up would be integrated with Stripe where we would have webhooks for successful payments for the user which will keep a track for the number of credits the user holds in the user's item. To accommodate this, we will have a DynamoDB record for each user with the id created on Cognito and use that as the reference.

Whenever the user casts the vote, the AppSync mutation would validate if the poll is free or paid, if paid, does the user have sufficient credits to cast the vote. In a sunny day scenario, the vote would increment the number by using the credit. For errors, the AppSync mutation would throw an error with relevant messages.

Additionally maintain a timeseries db for all transactions of credits (debit/credit)
