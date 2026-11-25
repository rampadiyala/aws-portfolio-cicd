# AWS Portfolio CI/CD

GitHub Actions syncs site/ to S3 and refreshes CloudFront.

## How to run

1. Create a private S3 bucket. 2. Create a CloudFront distribution with Origin Access Control for it, default root object index.html. 3. Add GitHub as an IAM OIDC provider and create a role limited to this repo's main branch, allowing s3:ListBucket, s3:PutObject, s3:DeleteObject on the bucket and cloudfront:CreateInvalidation on the distribution. 4. In GitHub add secret AWS_ROLE_ARN and variables AWS_REGION, BUCKET, DISTRIBUTION_ID. 5. Push to main.
