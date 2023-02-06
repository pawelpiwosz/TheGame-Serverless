# Week 5

## :link: Thread

[LinkedIn thread](https://www.linkedin.com/posts/pawelpiwosz_devops-aws-design-activity-7025588254343114752-mGiS)

## :page_with_curl: Requirements

Here is our task. We are assessed by the team of consultants. They asked for a few details about our approach. They know the application is serverless and is hosted in AWS. Tey want to know:

* What is the code approach? Do you use one monorepo or do you have different approach?
* What branching strategy do you use?
* What is your environments strategy? (here you have freedom to design as many envs as you wish, in fact you are responsible for DevOps too :) )
* How did you build the CI/CD What tools do you use?
* What quality gates are designed in the system?
* What deployment strategy did you select?
* What measurements you collect from CI/CD?
* How do you monitor CI/CD?
* What kind of security did you implement and how?

So, your task this week is to answer to these questions. Please, try to be very open and descriptive :) It is not exactly serverless task, however it is related to our serverless approach.

## :bookmark_tabs: Previous requirements

1. Client has to be logged in to vote
2. Client can vote only once
3. Client receives a confirmation of the action (or info that something went wrong)
4. Client can create many votings (for example 1 or 4 or... 15)
5. Some of these votings are tagged as free, some as paid with credit payments (for Frontend, this information must be visible in the voting tile, please reffer to my awesome graphics below :D )
6. User can decide if he wants to see paid votings
7. Users can buy credits using third party vendors (PayPal, credit cards). Our Client doesn't want to incorporate third party solution to have as less responsibilities in payments area as possible
8. The credits user has are visible for him on the "my profile" page
9. Each vote in paid voting costs one credit
10. Scheduled votings - start and end time of voting.
11. Client wants to send a few types of messages to people - reminders, updates, alerts. All these messages must be pushed to the app (not email, or any other channel)
12. Sseparation of data belongs to different Clients.
13. Clients also want to separate data per voting
14. Clients want to have dashboards with statistics (logged users, votes sent in time) and performance (how many votes per second, latency, errors, transaction execution time, etc)
15. New Client has expectations regarding the performance - details in repo.

## :thought_balloon: Discussions

Here are the threads, started by:

* [Vakhtang Koroghlishvili](discussions/VakhtangKoroghlishvili.md)
* [Matt Morgan](discussions/MattMorgan.md)
* [Sam Williams](discussions/SamWilliams.md)
* [Serhii Kryvoruchko](discussions/SerhiiKryvoruchko.md)
* [Dharmendra Negi](discussions/DharmendraNegi.md)

## :triangular_ruler: Architecture

You find all diagrams in *architecture* directory. It contains all diagrams created by Authors or me.

## :hammer: Services

This list contains **all** services mentioned by Authors. This time, the list covers also services from previous weeks.

* [Cognito](https://aws.amazon.com/cognito/)
* [S3 bucket](https://aws.amazon.com/s3/)
* [CloudFront](https://aws.amazon.com/cloudfront/)
* [Lambda](https://aws.amazon.com/lambda/)
* [Step Functions](https://aws.amazon.com/step-functions/)
* [Appsync](https://aws.amazon.com/appsync/)
* [API Gateway](https://aws.amazon.com/api-gateway/)
* [DynamoDB](https://aws.amazon.com/dynamodb/)
* [SQS](https://aws.amazon.com/sqs/)
* [SNS](https://aws.amazon.com/sns/)
* [Route53](https://aws.amazon.com/route53/)
* [ElastiCache](https://aws.amazon.com/elasticache/)
* [Amplify](https://aws.amazon.com/amplify/)
* [WAF](https://aws.amazon.com/waf/)
* [Timestream](https://aws.amazon.com/timestream/)
* [EventBridge](https://aws.amazon.com/eventbridge/)
* [Athena](https://aws.amazon.com/athena/)
* [CloudFormation](https://aws.amazon.com/cloudformation/)
* [CDK](https://aws.amazon.com/cdk/)
* [IAM](https://aws.amazon.com/iam/)
* [CodeCommit](https://aws.amazon.com/codecommit/)
* [CodeBuild](https://aws.amazon.com/codebuild/)
* [CodeDeploy](https://aws.amazon.com/codedeploy/)
* [IAM Identity Center (formely SSO)](https://aws.amazon.com/iam/identity-center/)
* 

Third party services

* [Stripe](https://stripe.com/)
* [PayPal](https://www.paypal.com/)
* GitHub Actions
* Gitlab
* Slack

## :bulb: Mindmap

![Mindmap for week 5](assets/week5-map.png)

## :chart_with_upwards_trend: Statistics

A little statistics about the thread. The final data here is updated around the moment of publishing the task of the new week.

| Key                             | Value |
| :------------------------------ | :---- |
| Reactions                       | 12    |
| Impressions                     | 3021:)|
| Comments (excluding my own :) ) | 8     |
| Reposts                         | 1     |
| Engaged                         | 6     |

## :coffee: Comments over coffee (or something else :smile: )

:one: *Anything except AWS CodePipline toolset* from Sam :) Love it :) However, I use CodePipeline, I prefer other tools.
:two: Engagement for security guys will go further
:three: The beauty of this game is in different scenarios you provide. Example: git trunk and git flow.
:four: Finally some nice engagement :D
