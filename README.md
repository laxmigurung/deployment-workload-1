# Kura Labs Cohort 5- Deployment Workload 1
## Intro to CI/CD
### Laxmi's Banking Application

1. Cloned the repository from the Kura Labs repository to my repository. I ran into a few issues when I ran 'git push'.
   - Permission denied and 403 Error when I tried to put my credentials from local.
   - created a new token in Git Hub, and set the expiration date to December 2025. I used this token to connect to the origin and successfully 

2. Now I created an EC2 instance to run the application.
   We need to install jenkins with all the required configurations to run this application in the EC2. Jenkins is an open-source automation server. This helped me to build my application. By looking into the console logs, I understood that Jenkins was building the package and checking if all the required bins and libraries for my application to run were set for a successful run.
   1. 
   

```
    $sudo apt update && sudo apt install fontconfig openjdk-17-jre software-properties-common && sudo add-apt-repository ppa:deadsnakes/ppa && sudo apt install python3.7 python3.7-venv
    $sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
    $echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
    $sudo apt-get update
    $sudo apt-get install jenkins
    $sudo systemctl start jenkins
    $sudo systemctl status jenkins

```

<img width="1506" alt="Screenshot 2024-07-27 at 11 14 21 PM" src="https://github.com/user-attachments/assets/cd4ddebc-1e78-48a2-a5d5-a294d62adb67">


7. After successfully completing the build (provide screenshot of successful build in documentation), download the contents of the repository (the one in your personal GitHub NOT the kuralabs repo!) and upload a zip file of the application it to AWS Elastic Beanstalk.
  
	a. First, follow the instructions in this [LINK](https://scribehow.com/shared/How_to_Create_an_AWS_IAM_Role_for_Elastic_Beanstalk_and_EC2__kTg4B7zRRxCp-aYTJc-WLg) for "How to Create an AWS IAM Role for Elastic Beanstalk and EC2" and create the two IAM roles as specified.

    b. Navigate to the AWS Elastic Beanstalk console page

    c. Navigate to the "Environments" page on the left side menu and click on "Create Environment"

    d. Create a "Web server environment" and enter the an Application name (Environment name should auto populate after that)

    e. Choose "Python 3.7" as the "Managed platform"

    f. "Upload your code" by choosing a "local file" and select the zipped application files you created earlier.

    g. Under "Presets", make sure that "Single instance (free tier eligible) is selected and then click "Next"

    h. Select the "Service role" and "EC2 profile" in the appropriate drop down menus and then click "Next"

    i. Select the default VPC and Subnet "us-east-1a" and then click "Next"

    j. Select "General Purpose (SSD) for "Root volume type" and assign it 10 GB.

    k. Ensure that "Single instance" is selected for the "Environment type" and that ONLY "t3.micro" is selected for instance types (remove all others if present) and then click "Next"

    l. Select 'BASIC' health reporting under the monitoring section. NOT "ENHANCED"!

    m. Continue to the "Review" page and then click "Submit".

    n. When the "environment is successfully launched", click on the link provided in the "Domain" and confirm that the application has deployed!

8. Document! All projects have documentation so that others can read and understand what was done and how it was done. Create a README.md file in your repository that describes:

	a. The "PURPOSE" of the Workload, 
	
	b. The "STEPS" taken (and why each was necessary/important, 
	
	c. A "SYSTEM DESIGN DIAGRAM" that is created in draw.io, 
	
	d. "ISSUES/TROUBLESHOOTING" that may or may have occured, 
	
	e. An "OPTIMIZATION" section for that answers the question: What are the benefits of using managed services for cloud infrastructure?  What are some issues that a retail bank would face choosing this method of deployment and how would you address/resolve them? What are other disadvantages of using elastic beanstalk or similar managed services for deploying applications?
	
	f. A "CONCLUSION" statement as well as any other sections you feel like you want to include.

The README.md is a markdown file that has unique formatting.  Be sure to look up how to write in markdown or use a txt to markdown converter. 


<img width="1506" alt="Screenshot 2024-07-28 at 12 42 49 AM" src="https://github.com/user-attachments/assets/6271bf7b-3d76-44a9-a9a6-f884181c3d0e">





