# Dharmendra Negi

*What is the code approach?*

1 each repo for FE and BE, in BE for DB infra and other one time things i would prefer one separate stack.(One repo can have more then one stack, depends on requirement)

*What branching strategy do you use?*

I will go with feature/* -> dev ->beta ->prod

*What is your environments strategy?* (here you have freedom to design as many envs as you wish, in fact you are responsible for DevOps too :) )

I will follow env as we defined branch, one env for Feature/*, Dev, Beta, Prod.  
Feature/* - for dev work and testing  
Dev - for QA to test  
Beta - for business team or third person to test before release.  
Prod - for end users

*How did you build the CI/CD What tools do you use?*

Any tool is fine like github, gitlab, bitbucket. If you ask preferences then: Github > Bitbucket > Gitlab > CodePipeline

*What quality gates are designed in the system?*

Linting > Unit test cases > EnE integration test(optional - depends on the services/use cases)> deployment

*What deployment strategy did you select?*

In the beginning - All at once deployment, but with the time and increase in traffic we can switch to Canary Deployments

*What measurements you collect from CI/CD?*

Test cases report, code analysis(optional)

*How do you monitor CI/CD?*

Email Notification and debug manually on failure

*What kind of security did you implement and how?*

Only provide required permission to the services to communicate with each other.  
Depend upon the service what security it requires, like for api endpoint enable WAF, avoid S3 as public.  
For FE minifying the code before deployment.
