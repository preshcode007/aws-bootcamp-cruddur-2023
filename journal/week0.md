# Week0 Architecture and Billing


## Required Homework
### 1. Installing AWS CLI
- __note: I am using VSCode, Cloudshell seems to make my laptop slow. I thik it has to do with my internet connection.__

- I installed the aws cli via the cmd ```curl https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" ```
- I unzipped the __awscliv2.zip file__ using ```unzip awscliv2.zip```

- I used the ```aws configure``` to put in credentials of the new user I created.

- using the  ```aws sts get-caller-identity``` I am able to check my account credential. The command acts like the ``whoami`` cmd on linux



## Homework Challenges
#### 1. Installing AWS Completer to my local machine via VSCode CLI
- I checked if aws_completer is in my local machine path using ``` which aws_completer```. It was located in /usr/bin/aws_completer

- I opened my Bash shell profile file which is the ```~/.bashrc``` file and I added ``` export PATH=/usr/local/bin/:$PATH``` to the end of the file. ![added PATH](assest/WEEK%200%20%20PATH%20added.png)

- The Bash shell profile file was then reloaded using the source ```~/.bashrc``` to effect the change.

- To enable aws_completer I added ```complete -C '/usr/local/bin/aws_completer' aws`` to the end of my Bash shell profile file (~/.bashrc) ![aws_completer installation complete](assest/WEEK%200%20%20AWS%20auto%20completer%20installation.png)

- __note: I am not using gitpod for now but vscode so I can save up on my gitpod free tier. __



