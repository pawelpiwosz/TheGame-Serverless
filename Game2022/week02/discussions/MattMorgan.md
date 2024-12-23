# Matt Morgan

Building on my [prior solution](https://www.linkedin.com/feed/update/urn:li:activity:7015449163140116480?commentUrn=urn%3Ali%3Acomment%3A%28activity%3A7015449163140116480%2C7015787446030278656%29&dashCommentUrn=urn%3Ali%3Afsd_comment%3A%287015787446030278656%2Curn%3Ali%3Aactivity%3A7015449163140116480%29)

The new requirements make me think AppSync might be better. One resolver can get all the elections. If the max amount of them is low (16?) then I'd probably just do client-side filtering, but otherwise, it's easy enough to make "isPaid" a query.

We'll handle payments via various client-side SDKs (Paypal, Stripe, etc) and provide a callback endpoint that will add credits to our user on successful payment.

When the user loads up the view, we'll hit the elections resolver and also have one that will pull back the user's credits and prior votes. This can be stored in DynamoDB with an overloaded partition. The partition key will be a user identifier and the sort key will be the entity type plus an identifier. Thus we can pull back the user profile and all votes in a single query, or we can update individual items. We are still able to ensure the user only votes for each election once by using a condition expression to ensure a vote for a particular election hasn't already happened.

As far as managing credits and votes, if we want to keep the application "functionless" (just for fun), we can use a synchronous express state machine to handle votes.

1. Is the vote paid? If not, skip the next two steps.
2. Does the user have a credit to spend? If not, throw an error.
3. Decrement the user's credits.
4. Record the user's vote.
5. Return feedback that the operation was a success.

I'd expect we'd want users to vote for one election at a time, but if they can submit many at once, then the step function would need to be altered to sum the paid elections and make sure the user has sufficient credits.

Cool app, maybe I'll try to build it.
