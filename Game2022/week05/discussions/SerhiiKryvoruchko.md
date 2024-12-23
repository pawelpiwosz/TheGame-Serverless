# Serhii Kryvoruchko

*What is the code approach? Do you use one monorepo or do you have different approach?*

Each service – one repo.  
For example: register service, vote service

*What branching strategy do you use?*

If the project is new, and we don’t have any tests, feature Branching.

*What is your environments strategy?* (here you have freedom to design as many envs as you wish, in fact you are responsible for DevOps too :) )

DEV and PROD

*How did you build the CI/CD What tools do you use?*

GitHub and set-up automatic deployment of Lambda function using GitHub actions

Or AWS CodeCommit and CodePipeline

*What quality gates are designed in the system?*

Automatic test

*What deployment strategy did you select?*

Blue-green deployment

*How do you monitor CI/CD?*

Email notifications, logs

*What kind of security did you implement and how?*

CSRF  
All infrastructure in private VPC  
DB's in the private subnet  
Only lambda functions can access the database using policy.

I wasn't able to conversation before. My idea is to use lambdas and RDS. According to current requirements, I think serverless Django will be a good option.
