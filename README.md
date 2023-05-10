# 🤖⏩ Synchronize Dev GitHub Action

This GitHub Action attempts to fast-forward the `dev` branch with the `master` branch. If it's unable to perform a fast-forward merge, it will create a new branch and open a pull request for manual review.

## Inputs

- `MAIN`: The name of the main branch. Default is `main`.
- `DEVELOP`: The name of the development branch. Default is `develop`.
- `BOT_NAME`: The name of the bot that will perform the operation.
- `BOT_EMAIL`: The email of the bot.
- `TOKEN`: The GitHub token. Please note that this token should have the necessary permissions to perform branch operations.
- `VERSION`: Only used when creating name of branch for PR. Defaults to version found in package.json 

## Usage

Here is a sample workflow file on how to use this action:

```yaml
name: 🤖⏩ Synchronize dev
on:
  push:
    branches:
      - master
  workflow_dispatch:

jobs:
  synchronize-dev:
    runs-on: ubuntu-latest
    steps:
      - name: Synchronize Dev Branch
        uses: knerd/sync-dev-action@v1
        with:
          MAIN: 'master'
          DEVELOP: 'dev'
          BOT_NAME: '🤖 workflows[bot]2023'
          BOT_EMAIL: 'devops+bot2023@org.com'
          TOKEN: ${{ secrets.GITHUB_TOKEN }}
