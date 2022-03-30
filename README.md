# simple-node-api

docker-simple-node-api is part of a small tutorial about github actions and heroku ci/cd pipeline

Fix:

In step 14, to create a Heroku's deploy action you need something like this in your yaml:
```
name: deploy

on:
  push:
    branches:
      - main
jobs:
  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
        - uses: actions/checkout@v2
        - name: Login to Heroku Container Registry
          env:
            HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
          run: heroku container:login
        - name: Build and Push
          env:
            HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
          run: heroku container:push -a ${{ secrets.HEROKU_APP_NAME }} web
        - name: Release
          env: 
            HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
          run: heroku container:release -a ${{ secrets.HEROKU_APP_NAME }} web
```

Resources: 

210 - CI/CD com GitHub Actions + DOCKER | theWiseDev CI/CD [https://www.youtube.com/watch?v=jBRw_WepZGA]

Tutorial step by the step - [https://like-jaw-394.notion.site/CI-CD-GitHub-Actions-Heroku-093d52e15d6f4a638f1c906e6127ec36]

simple-node-api repository - [https://github.com/tarikly/simple-node-api#simple-node-api]
