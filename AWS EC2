# Hosting Jenkins on AWS EC2 (Ubuntu 24.04)

This project documents how I successfully hosted a Jenkins server on an AWS EC2 instance using Ubuntu 24.04 and accessed it using PuTTY on Windows.

## 🧰 Tools Used
- AWS EC2 (Free Tier t2.micro)
- Ubuntu 24.04
- PuTTY & PuTTYgen
- Jenkins LTS

## 🪜 Steps Covered
1. Launched an EC2 instance
2. Connected via PuTTY using a `.ppk` key
3. Installed Java and Jenkins
4. Configured security group to allow port 8080
5. Accessed Jenkins dashboard through browser

✅ 1. Launched an EC2 Instance
Service Used: AWS EC2
Image: Ubuntu Server 24.04 LTS (Free Tier eligible)
Instance Type: t2.micro (Free Tier)

Steps:
Go to AWS EC2 → Launch Instance
Enter instance name: jenkins-server
Choose AMI: Ubuntu Server 24.04 LTS (HVM), SSD Volume Type
Select instance type: t2.micro
Create a new key pair:
    Name: jenkins-key
    Type: .pem           ##Download and save safely
In Network Settings:
    Auto-assign Public IP: Enabled
    Open port 22 (SSH)   ##Later we’ll open port 8080 (for Jenkins)
Click Launch Instance and Wait until status = Running

✅ 2. Connected via PuTTY using a .ppk key
PuTTY (on Windows) does not accept .pem files directly, so we Converted .pem to .ppk

Open PuTTYgen Click Load, select All Files, and choose your .pem key
Click Save Private Key → jenkins-key.ppk

Connect via PuTTY: Open PuTTY and enter Host Name: ubuntu@<your-public-ip>
Example: ubuntu@13.234.12.45
Go to Connection > SSH > Auth → Browse for jenkins-key.ppk Click Open → Accept SSH prompt
##You're now connected to the Ubuntu EC2 instance

✅ 3. Installed Java and Jenkins
Update system: sudo apt update && sudo apt upgrade -y
Install Java (required for Jenkins): sudo apt install openjdk-17-jdk -y
Add Jenkins key securely (apt-key is deprecated): curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null

Add Jenkins repository: echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

Install Jenkins: sudo apt update
              : sudo apt install jenkins -y

Start and enable Jenkins service: sudo systemctl start jenkins
                                 : sudo systemctl enable jenkins

✅ 4. Configured Security Group to Allow Port 8080
To access Jenkins via browser: Go to AWS EC2 Console → Instances and Select your instance → Go to Security > Security Groups Click Edit Inbound Rules
Add rule: 
    Type: Custom TCP and Port Range: 8080
    Source: My IP or Anywhere (0.0.0.0/0) for testing
Click Save

✅ 5. Accessed Jenkins Dashboard Through Browser
In your browser, go to: http://<your-ec2-public-ip>:8080
Example: http://13.234.12.45:8080
You’ll see the Jenkins unlock screen.

Get the admin password: sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Paste it into the browser → Continue
Choose: Install Suggested Plugins
Create an Admin User: Username, Password, Full name, Email
Click Save & Continue
🎉 You now have a fully working Jenkins server hosted on your EC2 Ubuntu instance!


