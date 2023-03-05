# Week 0 — Billing and Architecture

# **Todo List for week 0**

- Set MFA for Root Account

- Create an Admin User

- Use CloudShell

- Generate AWS Credentials

- Installed AWS CLI

- Create a Billing Alarm

- Create a Budget

### **Set MFA for Root Account**
Setting MFA for root account.

![MFA root acc](_docs/assets/images/root-acc-MFA.jpg)


### **Creating an Admin User:**
 To create a admin user, first we need to create a admin group. Users within this group will have all privileges to AWS account.
 IAM (Identity and Access management) Service is the place where we create users, groups, policies and roles for access aws account and different services within our aws account. 
Steps:
* Got to IAM console, Click on users group from the left side of the console and create group with name admin and assign aws manage policy AdministratorAccess.
* Before creating user there are 3 ways to give a user perrmission. Attach user to group, copy permissions, Attach policies directly. 
* In copy permission we can copy the permission of one user to another user or we can attach policies directly to users which is not a good practice and lastly the best one is assign user to a group. So, we already created the group name admin we now can assign our iam user to admin group which has AdministratorAccess.

![Admin user group](_docs/assets/images/IAM-group.png)


### **Use CloudShell**


### **Generate AWS Credentials & AWS CLI on gitpod**

Download the access key token from the IAM user and installed aws cli.

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install

```
Configure AWS CLI
Type aws configure on local terminal and a pop up will show up fill out your access key id, secret and default region and you're good to go.
If you're on gitpod we can add them to environment variables.

```
gp env AWS_ACCESS_KEY_ID="AKIA6NLPTWZYHZYO"
gp env AWS_SECRET_ACCESS_KEY="+KuB/gaddAisXs57tvDF9gCU9xomTcTfFbwE"
gp env AWS_DEFAULT_REGION="us-east-1"
```

### **Create a Budget**

There are two ways to create budget for our aws account through console and aws cli. I have created budget both ways.

Using CLI

```
aws budgets create-budget --account-id 990754292191 --budget file://aws/json/budget.json --notifications-with-subscribers file://aws/json/notifications-with-subscribers.json

```

I have used budget and notification json payload to send my budget data through aws cli API call which created me a budget of 5$ and an alert which will notify me via email whenever my cost exceeds threshold of 80% of my budget. 


### **Creating a billing alarm using cli**
Steps 
- Create a SNS topic 
- Create a subscription to that sns topic
- Create an alarm based on metric

```
aws sns create-topic --name cloud-billing-alarm
```
```
aws sns subscribe --topic-arn arn:aws:sns:us-east-1:990754292191:cloud-billing-alarm --protocol email --notification-endpoint info.alambiz@gmail.com
```
```
aws cloudwatch put-metric-alarm --cli-input-json file://aws/json/alarm_config.json
```

