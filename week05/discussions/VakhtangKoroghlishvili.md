# Vakhtang Koroghlishvili

Here, there are a wide range of choices and tactics we can discuss. One technique may be appropriate for one firm, while another is more appropriate for a different team. I would adopt the poly-repo strategy, which will subsequently make the CI/CD process simpler. Typically, I advise utilizing Git Flow, which is effective, particularly when we have parallel releases, etc. I would use AWS Code Commit, AWS Code Pipeline, and AWS Code Build to provision resources using the CloudFormation (alternatively, we can use Terraform, or there are lots of other options if a client requests a different tech scope).

The number of environments depends on a variety of factors, including cost, duration, disaster recovery strategy, and so on.

In terms of security, I'd make separate accounts for each environment (you build on the lower environment and promote artifacts to the higher environment via cross-account access). The Lambda function, Code Build, and every component will unquestionably be on a private virtual network.

I would use AWS CloudWatch filters to produce log-based metrics for CI/CD monitoring, and CloudTrail to follow events. There is much to discuss, and it is difficult to address all of it in a single comment.
