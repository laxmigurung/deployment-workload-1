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




Now, we use Elastic BeanStalk to deploy our application and make it live. Based on my understanding this is an infrastructure as a service as it provides services like monitoring, and autoscaling for the application.
Created two IAM roles. These IAM roles allow trusted identities to perform actions in AWS by assigning specific permissions to the services that are required to automate the application. It is trying to connect to our EC2 instance and the Beanstalk. 
  
	
    

<img width="1506" alt="Screenshot 2024-07-28 at 12 42 49 AM" src="https://github.com/user-attachments/assets/6271bf7b-3d76-44a9-a9a6-f884181c3d0e">



System Design Diagram


<img width="1117" alt="Screenshot 2024-08-01 at 11 36 17 PM" src="https://github.com/user-attachments/assets/3463af3f-5392-4fe4-9d2b-822fead4bbf1">

Based on my understanding
1. Jenkins helps to build the bins and libraries required for the application. It performs checks, and testing in the application folder with all the modules and determines if it is ready to be deployed or not.
2. Elastic Beanstalk provides an infra where our application is running using all the compute resources from the EC2 instance that it is connected to. 
In terms of scalability, I noticed how it keeps our application running and it has the ability to autoscale. By this when we have many client requests coming, this will autoscale to provide the users to send requests and use our app. But we also set the CPU usage to 10G, which means if it reaches the max limit, it will crash may be. 
