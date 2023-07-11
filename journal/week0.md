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

# AWS CLI

* Set Account ID  -- 
> gp env AWS_ACCOUNT_ID=$(aws sts get-caller-identity --query 
Account --output text)

* Create 1$ Budget --
- Copy Budget and Notifications Json from the AWS CLI documentation site
- Modify Budget to reflect it for 1$
- Modify Notification to use our own email Id.
- Run following command
> aws budgets create-budget \
    --account-id $AWS_ACCOUNT_ID \
    --budget file://aws/json/budget.json \
    --notifications-with-subscribers file://aws/json/budget-notifications-with-subscribers.json

* Create SNS Topic
> aws sns create-topic \
    --name billing-alarm

* Subscribe to SNS Topic
Copy the arn of topic which is outputed in previous command
> aws sns subscribe \
    --topic-arn <sns topic arn> \
    --protocol email \
    --notification-endpoint <your email id>

* Create Alarm
Use the input json
Run the command
> aws cloudwatch put-metric-alarm --cli-input-json file://aws/json/alarm-config.json