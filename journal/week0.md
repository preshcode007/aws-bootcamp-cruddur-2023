# Week0 Architecture and Billing


## Required Homework 
- ### hhhhss

## Homework Challenges
#### 1. Installing AWS Completer to my local machine VSCode CLI
- I checked if aws_completer is in my local machine path using ``` which aws_completer```. It was located in /usr/bin/aws_completer

- I opened my Bash shell profile file which is ```~/.bashrc``` and added ``` export PATH=/usr/local/bin/:$PATH``` to the end of the file.

- The Bash shell profile file was then reloaded using the source ```~/.bashrc``` to effect the change.

- To enable aws_completer I added ```complete -C '/usr/local/bin/aws_completer' aws`` to the end of my Bash shell profile file (~/.bashrc)

- __note: I am not using gitpod for now but vscode so I can save up on my gitpod free tier. Also AWS Cloudshell makes laptop slow, I thnk it has to do with my internet connection, hence another reason why I am using VSCode__

### 

