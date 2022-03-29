# simple-node-api

simple-node-api is part of a small tutorial about github actions and heroku ci/cd pipeline

Fix:

In step 14, to create a Heroku's deploy action you need something like this in your yaml:
```
name: deploy

on:
  push:
    branches:
      - master
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
        - uses: actions/checkout@v2
        - uses: akhileshns/heroku-deploy@v3.12.12
          with:
                heroku_api_key: ${{secrets.HEROKU_API_KEY}}
                heroku_app_name: "you-user-login-simple-node-api"
                heroku_email: "your-mail@adress.com"
```

Resources: 

209 - CI/CD com GitHub Actions: Deploy Automático no Heroku com Node.js | theWiseDev CI/CD [https://www.youtube.com/watch?v=jMO5L8OzlEU]

Tutorial step by the step - [https://like-jaw-394.notion.site/CI-CD-GitHub-Actions-Heroku-093d52e15d6f4a638f1c906e6127ec36]
