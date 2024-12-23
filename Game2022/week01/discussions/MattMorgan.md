# Matt Morgan

Frontend is an S3 static site behind Cloudfront.

For the backend, I'd authorize with Cognito and consider doing a direct API Gateway/DynamoDB integration. This will be a very fast integration that can support 10k RPS or more.

We can make the Cognito email (or another identifier) part of the partition key and use a condition expression to make sure each user can only vote once.

To give user feedback, we'd need to use some VTL. If we don't like that, we could use AppSync and write resolvers in JavaScript but the default service limits are lower so we'd have to pay more attention to scale (and also costs are slightly higher).

Components:  
Web/mobile view  
API  
User store  
Data store  

Services:  
S3  
CloudFront  
Cognito  
API Gateway or AppSync  
DynamoDB
