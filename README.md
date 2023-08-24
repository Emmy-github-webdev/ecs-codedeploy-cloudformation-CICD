# ecs-codedeploy-cloudformation-CICD

1. Create infra stack
2. Create ecs service stack
3. Create CodeDeploy stck
4. Create deployment group
`
aws deploy create-deployment-group \
     --cli-input-json file://Create_Deployment_Group_CLI_Param.json \
     --region us-east-2
`
5. Create deployment
`
aws deploy create-deployment \
     --cli-input-json file://Create_Deployment_CLI_Param.json \
     --region us-east-1
`
6. Create codepipeline stack