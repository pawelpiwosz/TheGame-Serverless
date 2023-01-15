# Antonio Lagrotteria

Use Amplify to host a React/Angular app to be hosted on S3 with a CloudFront distribution in front of. As custom resources add a Route53 with an alias record with CloudFront distribution and WAF webacl with default manager rules for protection.

Add Cognito authentication with user pool for login and JWT access token generation to be used by underlying APIs.

For simplicity, I'd use an API Gateway based on Lambdas for both Votings and Credits performing CRUD + more operations (such as filter by type) against a DynamoDB table. Authorization is managed by Cognito user pool authorization type.

About model schema. I would have 2 DynamoDB tables with voteId (or creditId) PK and userId:Type (or just userId) as SK with some additional attributes as name or amount.

Lambda functions can check if users are allowed to pay the vote it not. Probably orchestration here would help, but for now ll keep logic in the functions by reading info from tables.

Integrate Stripe in client and define a public API as Stripe webhook upon purchase complete, acknowledging successful payment with a SNS email notification.
