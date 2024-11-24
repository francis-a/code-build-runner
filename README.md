# CodeBuild runner

A simple CloudFormation template for using AWS CodeBuild as a custom GitHub actions runner.

Deploy with:

```bash
 aws cloudformation deploy --template-file code-build.cf.yaml --stack-name code-build-arm --no-fail-on-empty-changeset --capabilities CAPABILITY_IAM --parameter-overrides GitHubOAuthToken={Personall GitHub Access token} GitHubOrgName={Your GitHub org name} GitHubProjectName={GitHub project you want to build in CodeBuild}
```

The access token needs to be configured as described here: https://docs.aws.amazon.com/codebuild/latest/userguide/access-tokens-github.html

Once the stack is deployed a customer runner can be used in the configured `GitHubProjectName`.

`runs-on: codebuild-{GitHubProjectName}-${{ github.run_id }}-${{ github.run_attempt }}`