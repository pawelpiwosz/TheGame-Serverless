# Matt Morgan

Is it a monorepo? I don't feel like the app has gotten big enough that it would require more than one CloudFormation stack. As a CDK user, I prefer to put application code and infrastructure code together in one repo. If that makes it a monorepo, so be it, but to me it's just a good way to organize an application. ;)

Branching? Trunk-based development all the way. Any commit to trunk is built automatically, deployed to a non-prod environment, and then I'd likely use an approval step to go to prod.

For environments, the main idea here is that before applying a change to production, the identical change must've been applied to a non-prod environment in exactly the same way as prod (same IAM permissions, etc.). I also like to have an environment that is more open and available for experimentation. Really depends on the size of the team, but generally I like dev (more open permission-wise), qa (same as prod), prod. Only builds that have deployed successfully to qa can go to prod.

CI/CD tool could be CodePipeline, but I haven't fully warmed to it as it seems slow. I might give GitHub Actions a try.

Quality gates include linting, unit tests, possibly SAST, if a suitable tool can be found and paid for, automated e2e tests, and the successful deployment to qa as described above.

The deployment strategy is Continuous Delivery (mostly automated, but gated).

The metrics I'd collect are build success rate, time taken, frequency, and the ratio of builds to qa vs prod. Having many qa builds to one prod build suggests a problem.

Assuming I'm using GitHub Actions, monitoring is easy. I get an email notification (and/or slack if we're using it and the integration) when a build fails. We can also listen to CloudFormation events and use that to send notifications or collect additional metrics.

Security is a pretty broad topic. I think we've covered application security in earlier postings. For the pipeline security, I'd limit human access and attempt to make all changes with the pipeline. Here's where Code Pipeline starts to look a little better because the native security model is stronger than adding access keys to GitHub. It really depends on the customer and their comfort level as well as their expectations. Am I running this for them indefinitely? Do they have some kind of DevOps team that will get involved?
