# Sam Williams

For the paid / free ideas filtering I see two options:

1. DynamoDB with a separate partition for free and paid. This does mean if you want to see both then you have to do 2 queries.
2. one partition key but use compound sort keys  
pk = idea, sk = free#{date}#{ideaId}  
This allows you to get everything in a single query if required.

Which one to choose depends on the expected number of votes. With just 16 total ideas to vote on I'd go with option 2.  
Also assuming that there will be future filtering requirements on the ideas so partition design may need updating when those come.

One thing I'm not quite sure of yet is whether this is a multi-tenant app or a global vote/idea board? If it is multi-tenant then idea 2 could be adjusted to pk={tenantId} sk=idea#free#{date}#{ideaId}

Creating the ideas would be the same endpoint/mutation as last time but with some added params.

Payments - Stripe and Paypal hosted checkouts - on payment complete have a lambda webhook that adds the paid-for credits to a dynamo record for the user. maybe pk={userId}, sk=credits. You could even store the payments so they can see when and how much they topped up.

When a paid vote is cast, just decrement the credits in that dynamo record.

Api endpoint / GQL query for "Get My Details" which returns the user's details, credits and payment history. Could add a table of things they've voted on too.
