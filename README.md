$(aws cloudformation list-exports --query "Exports[?Name=='SamBucket'].Value" --output text)



aws cloudformation package --template-file sample.yaml --output-template-file sample-transformed.yaml --s3-bucket $(aws cloudformation list-exports --query "Exports[?Name=='SamBucket'].Value" --output text)
aws cloudformation deploy --template-file sample-transformed.yaml --stack-name sample-project  --capabilities CAPABILITY_IAM


{"repository":"smurphnturf/sample-project","ref":"refs/heads/feature/test-release-branch","base_ref":"","event_name":"create"}

{"repository":"smurphnturf/sample-project","ref":"refs/heads/feature/test-release-branch","base_ref":"","event_name":"delete"}

# Release

aws --profile shared-poweruser s3 cp pipeline.template.yaml s3://au-slyp-com-shared-cross-account-template-base-poc/shared-deployments/sample-project/release/sample-project-1.0.0/pipeline.template.yaml --acl private


{"repository":"smurphnturf/sample-project","ref":"refs/heads/release/sample-project-1.0.0","base_ref":"","event_name":"create"}
