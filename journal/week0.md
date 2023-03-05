# Week 0 — Billing and Architecture

# Todo List for week 0

Set MFA for Root Account

Create an Admin User

Use CloudShell

Generate AWS Credentials

Installed AWS CLI

Create a Billing Alarm

Create a Budget

### Set MFA for Root Account
Setting MFA for root account.

![MFA root acc](_docs/assets/images/root-acc-MFA.jpg)


### Creating an Admin User:
 To create a admin user, first we need to create a admin group. Users within this group will have all privileges to AWS account.
 IAM (Identity and Access management) Service is the place where we create users, groups, policies and roles for access aws account and different services within our aws account. 
Steps:
* Got to IAM console, Click on users group from the left side of the console and create group with name admin and assign aws manage policy AdministratorAccess.
* Before creating user there are 3 ways to give a user perrmission. Attach user to group, copy permissions, Attach policies directly. 
* In copy permission we can copy the permission of one user to another user or we can attach policies directly to users which is not a good practice and lastly the best one is assign user to a group. So, we already created the group name admin we now can assign our iam user to admin group which has AdministratorAccess.

![Admin user group](_docs/assets/images/IAM-group.png)


### Use CloudShell


### Generate AWS Credentials

### Installing AWS CLI on gitpod