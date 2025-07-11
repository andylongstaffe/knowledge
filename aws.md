
## SSO

    aws configure list (~/.aws/config)
    aws configure sso

    aws sts get-caller-identity

    aws s3 ls

    aws eks --profile qa list-clusters

See k8s.md for setting up k8s access via aws.
 
The login command needs to be run every day to refresh the session.

Additional info for sso configure command:

```
SSO session name (Recommended): <user>_DEV_SESSION
SSO start URL [None]: https://cloudbees.awsapps.com/start
SSO region [None]: us-east-1
SSO registration scopes [sso:account:access]: <click enter>After code select: cloudbees-compliance-dev from the list.CLI default client Region [us-east-1]:  us-east-1
CLI default output format [None]:  json
CLI profile name [infra-admin-700386920060]: ssodev
```

## ECR

    aws ecr get-login-password --profile ssodev --region us-east-1 | docker login --username AWS --password-stdin <id>.dkr.ecr.us-east-1.amazonaws.com

Manifest is not reliable on Dev/QA (something to do with helm charts) so this can be used to check the current tagged version of a service on a given env:

Checking deployed versioon

    crane auth login 700386920060.dkr.ecr.us-east-1.amazonaws.com -u AWS -p $(aws ecr get-login-password --profile dev --region us-east-1)
    crane config 700386920060.dkr.ecr.us-east-1.amazonaws.com/cbc/neo4j-connector:cbc-qa |  jq '.config.Labels' -r
