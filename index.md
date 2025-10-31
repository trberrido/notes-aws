# AWS Notes

## Amplify

Can use webhooks to trigger deployment from several repo.

No multi regions deployments.

```
version: 1
frontend:
  phases:
    preBuild:
      commands:
        - npm ci
        - git clone https://github.com/YOUR_USERNAME/YOUR_CONTENT_REPO.git content-repo
        - cp content-repo/index.md src/index.md
    build:
      commands:
        - npm run build
  artifacts:
    baseDirectory: _site
    files:
      - '**/*'
  cache:
    paths:
      - node_modules/**/*
```