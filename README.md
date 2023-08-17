# Helm Chart Linting Action

```yaml
name: Lint & Test Charts

on:
  push:
    branches:
      - "**"
      - "!main"

jobs:
  main:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v2
        with:
          fetch-depth: 0

      - name: Chart Testing
        uses: aruba-uxi/chart-testing-action@main
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-region: us-west-2
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          chart-directory: charts/android-version-service
          default-branch: main
          deployment-name: ${GITHUB_REPOSITORY#*/}
          skip-aws-setup: false
          skip-helm-setup: false
          skip-python-setup: false
          test-local: 
          test-production:
          test-staging:
```
