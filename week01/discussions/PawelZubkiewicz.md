# Pawel Zubkiewicz

A voting app needs to scale (I'm thinking about millions of users, perhaps at the same time?). Obviously, SPA hosted on S3+CloudFront and AuthN/AuthZ provided by Cognito. That's the easy part.

To make backed handle any kind of traffic, I'd use Storage First pattern: API Gateway directly integrated with SQS queue (without Lambda function in the middle).

Next Lambda function to read messages from the queue and save them into DynamDB.

To allow Clients to vote only once I'd put constraints on the DynamoDB table (ClientID). So technically user can vote as many times as he wishes but only the first time is counted. :smirk: You can easily block it on the frontend.

## Jason Wadsworth

Why not go directly to DynamoDB here, skipping SQS? Throttling concerns? I would think you’d have a good idea of expected volume and could scale it up, or even use pay per request. If you initially set your table’s read/write capacity to the high end of what you expect then DynamoDB will partition appropriately and you should then be able to handle the volumn even if you switch back to on demand.
