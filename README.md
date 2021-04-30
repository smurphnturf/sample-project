$(aws cloudformation list-exports --query "Exports[?Name=='SamBucket'].Value" --output text)



aws cloudformation package --template-file sample.yaml --output-template-file sample-transformed.yaml --s3-bucket $(aws cloudformation list-exports --query "Exports[?Name=='SamBucket'].Value" --output text)
aws cloudformation deploy --template-file sample-transformed.yaml --stack-name sample-project  --capabilities CAPABILITY_IAM


{"repository":"smurphnturf/sample-project","ref":"refs/heads/feature/test-release-branch","base_ref":"","event_name":"create"}

{"repository":"smurphnturf/sample-project","ref":"refs/heads/feature/test-release-branch","base_ref":"","event_name":"delete"}