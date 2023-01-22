# Week 3

## :link: Thread

[LinkedIn thread](https://www.linkedin.com/posts/pawelpiwosz_people-thegame-fun-activity-7020494076533706752-dahY)

## :page_with_curl: Requirements

* Our Client wishes to have scheduled votings. Another words, to comply with live events, Client wants to set each voting for specific time. For example, from 6 to 7pm on 23.02.2023. Users cannot send votes before the start and after the end of the voting. This must be reflected in FE but also BE needs to render the proper message.
* Client wants to send a few types of messages to people.
  * Reminders. User can add reminder to his profile and be notified 15 minutes before the voting (optional for user). At this point it is 1/0 action. User enables it for all and disables it for all votings.
  * Updates. These are information about upcoming campaigns / votings, etc. Kind of marketing consent. Also optional for users. Will be sent ad-hoc by Client (what means - we need to have admin panel now:) )
  * Alerts. 5 minutes before voting ends, notification must be sent to users, but only to those who are registered to the voting, but didn't voted yet.

All these messages must be pushed to the app (not email, or any other channel).

## :bookmark_tabs: Previous requirements

* Client has to be logged in to vote
* Client can vote only once
* Client receives a confirmation of the action (or info that something went wrong)
* Client can create many votings (for example 1 or 4 or... 15)
* Some of these votings are tagged as free, some as paid with credit payments (for Frontend, this information must be visible in the voting tile, please reffer to my awesome graphics below :D )
* User can decide if he wants to see paid votings
* Users can buy credits using third party vendors (PayPal, credit cards). Our Client doesn't want to incorporate third party solution to have as less responsibilities in payments area as possible
* The credits user has are visible for him on the "my profile" page
* Each vote in paid voting costs one credit

## :thought_balloon: Discussions

Here are the threads, started by:

* [Antonio Lagrotteria](discussions/AntonioLagrotteria.md)
* [Dharmendra Negi](discussions/DharmendraNegi.md)
* [Matt Morgan](discussions/MattMorgan.md)
* [Jones Zachariah Noel](discussions/JonesZachariahNoel.md)


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

Third party services

* [Stripe](https://stripe.com/)
* [PayPal](https://www.paypal.com/)

## :bulb: Mindmap

![Mindmap for week 3](assets/week3-map.png)

## :chart_with_upwards_trend: Statistics

A little statistics about the thread. The final data here is updated around the moment of publishing the task of the new week.

| Key                             | Value |
| :------------------------------ | :---- |
| Reactions                       | 16    |
| Impressions                     | 1733  |
| Comments (excluding my own :) ) | 10    |
| Reposts                         | 0 :(  |
| Engaged                         | 5     |

## :coffee: Comments over coffee (or something else :smile: )

:one: I definitely need to work on marketing side of this game :)
:two: The designs didn't change much. I think, Antonio provides most of changes comparing to previous design.
:three: Next challenge will be a little bit different, stay tuned :)
:four: I still have a lot of thrill when looking on my wall: "maybe somebody commented? maybe there is a new design?". Don't make me feel sad :)
