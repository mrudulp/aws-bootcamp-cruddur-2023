# Week 0 — Billing and Architecture

* Create IAM user to access terminal
* Install AWS CLI (https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
    - Install AWS on gitpod by following instructions for linux machine
    - Add Command completion by following instructions over [here](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-completion.html#cli-command-completion-linux)
* Create User with admin access and cli access
    - For Admin Access create group with Admin permission
    - For cli access create user then go to security credentials and create access key. Select Local Development while creating access.
* Set access Keys as environment variable ¨
    - export AWS_ACCESS_KEY_ID=""
    - export AWS_SECRET_ACCESS_KEY=""
    - export AWS_DEFAULT_REGION="eu-west-1"