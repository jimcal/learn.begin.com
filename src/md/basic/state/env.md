---
layout: basic.11ty.js
title: serverless web dev training with architect
---

# Environment variables

Environment variables allow us to parameterize sensitive state like third party API keys and URLs without hard coding into our application code. 

1. Create a new app on Begin

[![Deploy to Begin](https://static.begin.com/deploy-to-begin.svg)](https://begin.com/apps/create?template=https://github.com/begin-examples/learn-static-oauth)

> Make note of the `staging` and `production` URLs you will need them later

2. Create *three* OAuth applications on GitHub [following these instructions](https://developer.github.com/apps/building-oauth-apps/creating-an-oauth-app/) …this ensures totally isolated systems for `testing`, `staging` and `production` environments

| Application name  | Homepage URL                      | Authorization callback URL               |
|------------------ |---------------------------------- |----------------------------------------- |
| My App Local      | http://localhost:3333                            | http://localhost:3333/login              |
| My App Staging    | https://foo-123-staging.begin.app | https://foo-123-staging.begin.app/login  | 
| My App Production | https://foo-123.begin.app         | https://foo-123.begin.app/login          |


3. To dev OAuth locally create a file in the root of the project directory called `.arc-env` and add the GitHub Client ID, Secret Key and redirect values to it for your local testing environment:

```bash
@testing
GITHUB_CLIENT_ID xxx
GITHUB_CLIENT_SECRET xxx
GITHUB_REDIRECT http://localhost:3333/login
```

> Ensure `.arc-env` **does not** get committed to revision control by adding it to `.gitignore`

4. Update the app on Begin.com with environment variables for `staging` and `production` so our deployed app has keys

5. Proceed to [implement OAuth](/basic/state/oauth)
