
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
