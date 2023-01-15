# Ryan Teague

Agree with most that a S3 spa wth API Gateway endpoints and Cognito Authorization is the way to go. For live poll results use web sockets (amplify or api gateway) and integrate a Stripe Endpoint for user credit processing.

To me it's important that the database foundationally is setup for success. I like to keep each poll on separate partitions to avoid hot keys and conditional checks to handle concurrency.

When a vote is submitted an entry is made into the UserVotingFacet with a conditional check that the PK doesn't exist to adhere to the only one vote per poll constraint. I would wrap this in a transaction where we were also entering a debit into the user credit history facet and sending a incr -1 to the user bank facet with a conditional check that user bank facet value is greater than 0.

On success a +1 incr write to the poll option facet, I don't like a transaction here as high concurrency requests on same partition will cause too much transaction conflict noise so you will need to build in throttling exception handling logic for the incr.

For the UI create a index to query polls by type and closing date where closing date is greater than today. Only query paid index for paying clients and merge the results.

[Structure](../assets/ryanteague.png)
