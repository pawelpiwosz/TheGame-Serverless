# Sam Williams

*What is the code approach? Do you use one monorepo or do you have different approach?*

It depends on the size and experience of the team. Assuming a skilled team of 5 devs, separate FE repo, then a backend repo.

I would organise it in a way that the core functionality and reporting were somewhat isolated, so if it gets too much, they can be separated.

*What branching strategy do you use?*

Github Flow - kind of links with the next question  
Would review this over time if/when the team and project grows

*What is your environments strategy?*

Production environment is as locked down as possible. Read access is limited to the lead dev. Write access is only temporarily granted and that "incident" is documented. If we handle any card details that would all live in a "PCI Prod" account to shelter the rest of prod from PCI regulation.

There would be a feature AWS account where feature branches can be deployed to. Each feature branch gets it's own temporary deployment.

Also each dev has a personal AWS account to use for connecting to their local dev envonrment.

*How did you build the CI/CD What tools do you use?*

Anything except AWS CodePipline toolset
Probably Github Actions
On PR deploy to features account.

*What quality gates are designed in the system?*

local integration and acceptance testing - test against the developer's account. Unit tests if complex business logic in a function.

CI/CD post feature deploy - integration testing and e2e testing all automated. If it fails, it blocks the PR.

Run automated test in prod after merge deployment completion.

If we can afford it - a tester who does some manual testing and then turns those into automated tests.

*What measurements you collect from CI/CD?*

latency of certain key requests, total Lambda invocations and runtime

In prod, use a tool like Sedai to monitor any changes between releases.

*How do you monitor CI/CD?*

Slack integration  
Dashboard  
Email notification for major issues ( test failing after being deployed to prod)  

*What kind of security did you implement and how?*

Multi accounts  
AWS SSO for internal team access  
cognito for customer access  
