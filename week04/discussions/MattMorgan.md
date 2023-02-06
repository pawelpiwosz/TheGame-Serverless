# Matt Morgan

Not sure I follow "25% os users" - do you mean we need to support mobile? If so, I'm not seeing anything here that really needs native features, so we can probably keep it simple by embedding a web view. This would make it easy to support Android as well.

1-2M users daily is no big deal for serverless architectures. To achieve this SLA, we could go multi-region, but really I'd advise against that because we'll have very good reliability without doing it. Either way, we can set ourselves up for global availability with a global DynamoDB table, and of course, we're using CloudFront for web assets.

If the customer insists on multi-region failover, we can deploy the same stack to multiple regions and combine health checks with route53 to fail over to backup regions. With a global table, we wouldn't have data disruptions or cutover issues and the cost of the backup regions would be negligible - though deployments are now a little slower (as slow as the slowest region) and more complex.

For reports and metrics, we can stream from the database to S3 and use Athena or more complex BI tools as needed.
