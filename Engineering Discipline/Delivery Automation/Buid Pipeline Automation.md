# Build Pipeline Automation

Any code change may trigger a build, and any successful build can be deployed to staging automatically.
#
# Implementation - 01

### Scope
Following implementation is applicable for the projects that uses AWS to manage their CI/CD pipeline.

### Tools
- [GitHub](https://github.com)
- [AWS Code Build](https://aws.amazon.com/codebuild/)
- [AWS Code Pipeline](https://aws.amazon.com/codepipeline/)

### How?
- Create Code Build projects for frontend and backend projects
- [Optional] If the backend consists of multiple microservices, create Code Build project for each
- Link Code Build project with GitHub via Webhook (Configure from Code Build console)
- Create Code Pipeline projects for Production/Staging/Dev environmets
- Link Code Build projects in each Code Pipeline as steps (Parallel/Serial)
- Link the GitHub branch (e.g. Production/Staging/Dev) that corresponding CodePipeline should be triggered

### Tips
- Configure CodeBuild status update to be published to GitHub
- Configure manual approvals if you think both frontend and backend deployments are unnecessary for each release
- Add manual approval steps in the Code Pipeline particularly for production release
- Send emails to interested parties when the CodePipeline is finished
- Canary deployment can be added by ticking off canary deployment check on the microservice (AWS API Gateway Level)

### Challenges
- Rollbacks are not yet directly supported as part of CodePipeline
- We need to use CodeDeploy project to configure rollbacks with the pipeline

### Example
<img width="1390" alt="screen shot 2019-02-01 at 11 05 40 am" src="https://user-images.githubusercontent.com/2338919/52104623-71f9b300-2611-11e9-9988-43e8b3da8c1a.png">
