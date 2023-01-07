# Sam Williams

Static front end with login using Cognito.
Simple API gateway with a vote endpoint.

DynamoDB table with a record of votes. Schema something like

PK: ideaId  
sk: userId (from cognito)  
.... other fields if needed

Lambda API checks if that record exists (idea && user) if not, then create record and tell the they voted, else tell them they already voted. All synchronous for now to keep it simple.

API to query on ideaId to get the total votes for an idea.

## Timothy Doolan

I would support this with only one addition. Leading keys IAM policy for the sort key. That way users can only amend their vote.. so small change needed to signup. We create record in DynamoDB with no voting intention. Custom Lambda attached to Cognito. Then subsequent write api calls to db must be for the authorised user. Naturally the vote checker must now check for a value not just a record. We can do this with a query.

[Link to docs](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html)

And to improved DynamoDB workload. Mabey the table name is the idea. Multiple ideas = multiple tables. Primary key is Cognito user is that gives high cardinality and inproves sharding ect. No hot partitions. Then sort key is intent. If we had multiple choices in voting intention. Sort key would then be the easiest way to query the results per table (idea). “Speed greasy speed” as mickey would say ;-).

## Sam Williams

If you did that you'd have to do a new deployment for each idea or dynamically generate tables which isn't something I've seen dome much.

Having a PK = ideaId, SK = userId you'd end up with a table like this:

pk sk  
idea1 userId1  
idea1 userId2  
idea2 userId1  
idea1 userId3  
idea3 userId2  

If you get a new idea = new PK = new partition

If a user tries to vote on an idea twice, it would overwrite the first vote. (if that was the desired behaviour)

If you went with pk = userId, sk = vote intent, what stops a user from voting twice on an idea with different intents? The two records would have a different composite key.

Also if there was a table for each idea, there would be no way to get "all votes for a user" without querying every table.
With a single table design you just have a GSI with userId and ideaId switched and then you can get all votes for a user.

## Timothy Doolan

Yep, you're right, all valid concerns. Hence I copped out with a “Mabey” ha ha. It was a cheap attempt to release the primary key to be more performant. Querying for large volumes of data in one table will hurt at scale.. would be worth modelling in a real world scenario.
