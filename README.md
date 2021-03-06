# Setup

```
$ npm install
$ npm install -g nodemon
$ npm i -g babel-cli
```

## Setup mysql
Installer: https://dev.mysql.com/downloads/mysql/

IMPORTANT : For the development environment, set the root user password to "community-db-common-test-password".

## Import sample database and data

Install:

- $ npm run db-install
Or
- $ npm run db-install-with-seed

Reinstall:

- $ npm run db-reinstall
Or
- $ npm run db-reinstall-with-seed

## install NVM (node version manager)
Windows: https://github.com/coreybutler/nvm-windows/releases
Mac: https://github.com/creationix/nvm/blob/master/README.md#installation

- nvm install 8.11.4
- nvm use 8.11.4

### Fix NVM

Windows? do:
- open node_modules/pre-push/index.js
- find `if (!this.npm)`
- right after if block, put:
`this.npm += ".cmd";`

## Adding new flow type definition
In order to avoid flow type errors, you can fetch definitions for popular modules from flow-typed.

`npm run flow-typed-add express@4`

## How to develop new features

- Fork this repo
- Click on `Clone or download` button
- Open your terminal:

```
# Replace XXX with what you just pasted
$ git remote add my-fork FORK_URL

# Create a new feature branch ()
$ git checkout -b BRANCH_NAME

# Make changes in the code base ...

# Check for formatting
$ npm run lint

# Check for flow types
$ npm run flow

# Run unit tests
$ npm run test

# If all checks (lint, flow, test) are passing, add updated files to staging
$ git add src/server.js

# Commit your changes
$ git commit -m "added new auth method"

# When you are ready to create a PR, push your changes to your fork
$ git push -u my-fork BRANCH_NAME

# Go to github, open your forked repository page
# Click on `New pull request` button
# Make sure you see base: dev, and original repo name on the left
#   And BRANCH_NAME, and your fork's name on the right.
# Hit `Create pull request` button

# Once PR is created, make sure Travis build passes. Then ask other developers to review your code.
