# ecs-codedeploy-cloudformation-CICD

1. Create infra stack
`
aws cloudformation create-stack --capabilities CAPABILITY_IAM --stack-name mystack-network --template-body file://infra.yml
`
2. Create ecs service stack
`
aws cloudformation create-stack --capabilities CAPABILITY_AUTO_EXPAND
 --stack-name mystack-service --template-body file://service-stack.yml --parameters ParameterKey=StackName,ParameterValue=mystack-network 
`
4. Create CodeDeploy Application stack
`
aws cloudformation create-stack --capabilities CAPABILITY_IAM --stack-name mystack-codedeploy-application --template-body file://Create_CodeDeploy_Application.yaml
`
3. Create deployment group
`
aws deploy create-deployment-group \
     --cli-input-json file://Create_Deployment_Group_CLI_Param.json \
     --region us-east-2
`
4. Create Deployment
`
aws deploy create-deployment \
     --cli-input-json file://Create_Deployment_CLI_Param.json \
     --region us-east-2
`
5. Create deployment group
`
aws deploy create-deployment-group \
     --cli-input-json file://Create_Deployment_Group_CLI_Param.json \
     --region us-east-2
`

6. Create codepipeline stack
`
aws cloudformation create-stack --capabilities CAPABILITY_IAM --stack-name mystack-codepipeline --template-body file://Create_CodePipeline.yaml
`