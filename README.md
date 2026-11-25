# AWS Portfolio CI/CD

A portfolio page with a GitHub Actions workflow for deployment to AWS.

## Features

- Syncs `site/` to S3 on push to main
- Refreshes the CloudFront cache
- Uses an IAM role through OIDC

## Tech stack

HTML, GitHub Actions, S3, CloudFront, IAM

## How to run

Preview: `npm start` (needs Python 3), then open http://localhost:8000.

## AWS setup

1. Create a private S3 bucket.
2. Create a CloudFront distribution with Origin Access Control and default root object `index.html`.
3. Add GitHub as an IAM OIDC provider. Create a role limited to this repository's main branch, allowing s3:ListBucket, s3:PutObject and s3:DeleteObject on the bucket, and cloudfront:CreateInvalidation on the distribution.
4. In GitHub, add the secret `AWS_ROLE_ARN` and variables `AWS_REGION`, `BUCKET`, `DISTRIBUTION_ID`.
5. Push to main or re-run the workflow.

## Project files

- `site/` - website
- `.github/workflows/deploy.yml` - deployment workflow

## Notes

Deployment needs the AWS setup above. AWS may charge for usage.

## License

MIT. See [LICENSE](LICENSE).
