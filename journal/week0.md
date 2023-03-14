# Week0 Architecture and Billing


## Required Homework
### 1. Installing AWS CLI
- __note: I am using VSCode, Cloudshell seems to make my laptop slow. I thik it has to do with my internet connection.__

- I installed the aws cli via the cmd ```curl https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" ```
- I unzipped the __awscliv2.zip file__ using ```unzip awscliv2.zip```

- I used the ```aws configure``` to put in credentials of the new user I created.

- using the  ```aws sts get-caller-identity``` I am able to check my account credential. The command acts like the ``whoami`` cmd on linux

### 2. Creating a Billig Alarm
- I have configured my AWS CLI profile with the name __myprofile__. By doing this, my AWS credentials have been stored in a file named __myprofile__, which I can use as a parameter for the ```--profile``` option instead of directly exposing my access key and secret key. To configure this profile, I ran the command ```aws configure --profile myprofile```.

- During the initial setup of my Billing Alarm on Github, I received an error message indicating that the designated SNS Topic for the alarm action could not be found ![]() .

- In an effort to resolve this issue, I proceeded to create an SNS Topic titled __BillingTopic__ using the AWS command ```aws sns create-topic --name BillingTopic --region us-east-1 --output json``` .

- Further along the configuration process of my Billing Alarm, I encountered another error related to SNS functionality, which required me to add a Subscription to the SNS Topic I had previously created.

- To accomplish this, I utilized the following AWS command ```aws sns subscribe --topic-arn arn:aws:sns:us-east-1:810909660778:BillingTopic --protocol Email --notification-endpoint okiemenprecious@gmail.com --region us-east-1 --output json```.

- After encountering and addressing the previous SNS error in my Billing Alarm setup, I proceeded to recreate the billing alarm and provided the '--alarm-actions' parameter with the 'BillingTopic' SNS Topic, which resulted in a successful configuration process. 

- The AWS command I utilized was 
```aws cloudwatch put-metric-alarm --alarm-name MyBillingAlarm --alarm-description "My billing alarm" --actions-enabled --metric-name EstimatedCharges --namespace AWS/Billing --statistic Maximum --period 21600 --evaluation-periods 2 --threshold 5 --comparison-operator GreaterThanOrEqualToThreshold --dimensions Name=Currency,Value=USD --alarm-actions arn:aws:sns:us-east-1:810909660778:BillingTopic --ok-actions arn:aws:sns:us-east-1:810909660778:BillingTopic --profile myprofile --region us-east-1 --output json```

### 3. Creating a Cost Budget and a Credit Budget 
- During the process of creating a cost and credit budget, I encountered several challenges that impeded my progress. These obstacles included:

1. Difficulty in generating the appropriate JSON files for each budget.
2. Inability to accurately parse the required parameters and arguments for the Visual Studio Code (VSCode) Command Line Interface (CLI).
3. Over-reliance on ChatGPT to generate the correct code based on my prompts.

- After overcoming several obstacles, I was able to create the cost and credit budget using the terminal with the correct JSON file for each budget, after investing approximately 4 hours in the process.

- - I created the cost budget using 
```aws budgets create-budget  --account-id 810909660778 --budget file://aws-json/budget/budget-actual-spend.json  --notifications-with-subscribers  file://aws-json/notification.json --region us-east-1```




## Homework Challenges
#### 1. Installing AWS Completer to my local machine via VSCode CLI
- I checked if aws_completer is in my local machine path using ``` which aws_completer```. It was located in /usr/bin/aws_completer

- I opened my Bash shell profile file which is the ```~/.bashrc``` file and I added ``` export PATH=/usr/local/bin/:$PATH``` to the end of the file. ![added PATH](assest/WEEK%200%20%20PATH%20added.png)

- The Bash shell profile file was then reloaded using the source ```~/.bashrc``` to effect the change.

- To enable aws_completer I added ```complete -C '/usr/local/bin/aws_completer' aws`` to the end of my Bash shell profile file (~/.bashrc) ![aws_completer installation complete](assest/WEEK%200%20%20AWS%20auto%20completer%20installation.png)

- __note: I am not using gitpod for now but vscode so I can save up on my gitpod free tier. __


#### 2. Deleting all my setup from the IAM Accounts, AWS Organisation, Billing, CloudWatch, s3 buckets ...everything and try to automate my setup via Infrastructure as code.
- I will be making use of a new tool __org-formation__ as one of the open source tools I will be using for the  automation process

