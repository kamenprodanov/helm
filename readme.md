## Architecture
- EKS Cluster: helmdeploy (eu-central-1)
- Private ECR for container images
- VPC Endpoints for secure ECR access (no NAT Gateway needed...originally tried pulling the image from outside, but did not have EIP and did not want to create such)
- GitHub Actions for automated deployment

## Issues Encountered & Solutions
**Image Pull Failure**: Nodes lacked internet connectivity
   - Solution: Implemented VPC endpoints for ECR (Did not want to create EIP)


## Cost Optimization
- Used VPC endpoints instead of NAT Gateway - Cheaper

## Setup Instructions
Created EKS with the Auto mode for a faster setup.
GitHub account with OIDC configured for AWS authentication
Configure VPC Endpoints for ECR (ECR API and ECR Docker endoints and S3 Gateway endpoint)
Pulled nginx from Docker hub, tagged it and then pusshed it to ECR

Configure AWS OIDC for GitHub Actions
Commented "on push" deployment as I was doing too many changes, so I only left it on a manual run.

## Dump command:
helm template my-nginx-release . --namespace staging

## Cleanup
Resources deleted on [10.26.2025] to avoid ongoing costs.

## Screenshots from the deployment logs and the AWS resources will be sent over email.
