# 🐧 DevOps Day 1 – Linux Commands
 contains basic Linux commands practiced as part of DevOps Day-1.

---

## 📁 1️⃣ Directory Commands

- `pwd` – Print Working Directory (Shows current location)
- `ls` – List files and folders
- `ls -l` – Detailed list format
- `ls -a` – Show hidden files
- `cd foldername` – Change directory
- `cd ..` – Go to parent directory
- `cd ~` – Go to home directory
- `mkdir newdir` – Create new directory
- `rmdir newdir` – Remove empty directory

---

## 📄 2️⃣ File Commands

- `touch file.txt` – Create empty file
- `vim file.txt` – Open file in Vim editor
- `cat file.txt` – Display file content
- `cp source.txt dest.txt` – Copy file
- `mv old.txt new.txt` – Move or rename file
- `rm file.txt` – Delete file
- `history` – Show previously used commands

---

## ⭐ 3️⃣ Wildcard Commands

- `ls *.txt` – List all `.txt` files
- `rm *.txt` – Remove all `.txt` files
- `ls file?.txt` – Match exactly one character

---

## 📦 4️⃣ Ubuntu Package Commands

- `sudo apt update` – Update package list
- `sudo apt upgrade -y` – Upgrade installed packages

---

## 🔐 5️⃣ SSH Commands

- `sudo apt install openssh-server` – Install SSH
- `sudo systemctl status ssh` – Check SSH status
- `sudo systemctl start ssh` – Start SSH service
- `sudo systemctl enable ssh` – Enable SSH at boot

---

## ⚙️ 6️⃣ Additional Important Commands

- `clear` – Clear terminal screen (Shortcut: **Ctrl + L**)
- `head file.txt` – Show first 10 lines
- `tail file.txt` – Show last 10 lines
- `tail -f file.txt` – Live monitoring
- `chmod +x script.sh` – Make file executable
- `ps` – Show running processes
- `top` – Real-time process monitoring
- `ip a` – Show IP address
- `ping google.com` – Check network connectivity

---


# 🐳 DevOps Day 2 – Docker 

This repository branch contains Day-2 focused on Docker installation, configuration, and container management.

------------------------------------------------------------
📌 OBJECTIVE
------------------------------------------------------------

The objective of Day-2 is to understand Docker fundamentals including:

- Installing Docker on Ubuntu
- Running containers
- Managing images
- Port mapping
- Container lifecycle management

------------------------------------------------------------
🛠 STEP 1 – Install Docker
------------------------------------------------------------

Update system:

sudo apt update

Install Docker:

sudo apt install docker.io -y

Start Docker service:

sudo systemctl start docker

Enable Docker at boot:

sudo systemctl enable docker

Verify Docker:

docker --version
docker info

------------------------------------------------------------
📦 STEP 2 – Basic Docker Commands
------------------------------------------------------------

docker images  
→ Shows downloaded Docker images

docker pull nginx  
→ Download nginx image from Docker Hub

docker run nginx  
→ Run container from image

docker run -d nginx  
→ Run container in background mode

docker ps  
→ Show running containers

docker ps -a  
→ Show all containers (including stopped)

docker stop <container_id>  
→ Stop running container

docker rm <container_id>  
→ Remove container

docker rmi <image_name>  
→ Remove image

------------------------------------------------------------
🌐 STEP 3 – Run Nginx Container
------------------------------------------------------------

Run Nginx with port mapping:

docker run -d -p 8080:80 nginx

Open browser:

http://<server-ip>:8080

Example:
http://192.168.150.129:8080

------------------------------------------------------------
📂 STEP 4 – Docker File Structure Understanding
------------------------------------------------------------

Image → Blueprint  
Container → Running instance of image  
Docker Hub → Online image repository  
Port Mapping → Connect container port to host port  

Example:

-p 8080:80  

Host Port → 8080  
Container Port → 80  

------------------------------------------------------------
🎯 LEARNING OUTCOME
------------------------------------------------------------

✔ Installed Docker successfully  
✔ Understood Docker architecture  
✔ Pulled images from Docker Hub  
✔ Ran containers  
✔ Used port mapping  
✔ Managed container lifecycle  
✔ Practiced basic Docker commands  

------------------------------------------------------------
📸 OUTPUT SCREENSHOTS
------------------------------------------------------------

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-13 230832.png)

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-14 000526.png)

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-14 001509.png)

---------------------------------------
DEVOPS DAY 3
GIT SSH CONFIGURATION AND BRANCH WORKFLOW
-----------------------------------------

Repository: devops

Objective:
To configure Git with SSH authentication and create a new branch for development work.

----------------------------------------
Step 1: Git Configuration
----------------------------------------

Configured Git username and email globally:

git config --global user.name "soumi04"
git config --global user.email "soumyakathiravan@gmail.com"

Verified configuration using:
git config --list

Purpose:
This ensures that all commits are recorded with correct author details.

----------------------------------------
Step 2: SSH Key Generation
----------------------------------------

Generated SSH key using:

ssh-keygen -t ed25519 -C "soumyakathiravan@gmail.com"

The public key was saved in:
~/.ssh/id_ed25519.pub

Displayed the public key using:
cat ~/.ssh/id_ed25519.pub

Added the SSH public key to GitHub under:
Settings → SSH and GPG Keys

Tested SSH connection using:
ssh -T git@github.com

Authentication was successful.

Purpose:
SSH allows secure communication between local Ubuntu system and GitHub without using a password each time.

----------------------------------------
Step 3: Repository Cloning
----------------------------------------

Cloned the GitHub repository using SSH:

git clone git@github.com:soumi04/devops.git

Navigated into repository:
cd devops

Verified repository contents using:
ls -a

Confirmed .git directory exists, which indicates it is a Git repository.

----------------------------------------
Step 4: Branch Creation
----------------------------------------

Checked existing branches:
git branch

Created a new branch:
git checkout -b new-branch

Verified branch switch:
git branch

The active branch is marked with (*).

----------------------------------------
Step 5: File Creation and Documentation
----------------------------------------

Created a new text file:

touch documentation.txt
nano documentation.txt

Added detailed workflow explanation inside the file.

----------------------------------------
Conclusion:
----------------------------------------

Git was successfully configured.
SSH authentication was set up and tested.
Repository was cloned securely.
A new branch was created for independent development.
Basic branch workflow was practiced successfully.

Status:
Configuration and branch setup completed successfully.

------------------------------------------------------------
📸 OUTPUT SCREENSHOTS
------------------------------------------------------------

![]()

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-14 090903.png)

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-14 002317.png)

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-14 002354.png)

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-14 002441.png)

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-14 000526.png)


# 🚀 DevOps Day 4 – Jenkins CI/CD with Docker

------------------------------------------------------------
OVERVIEW
------------------------------------------------------------

This project demonstrates the implementation of a CI/CD pipeline using Jenkins and Docker.
The objective is to automate Docker image building and container deployment using Jenkins integrated with GitHub.

------------------------------------------------------------
STEP 1 – Install Java (Required for Jenkins)
------------------------------------------------------------

sudo apt update
sudo apt install openjdk-21-jre -y
java -version

------------------------------------------------------------
STEP 2 – Install Jenkins
------------------------------------------------------------

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key

echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt update
sudo apt install jenkins -y


------------------------------------------------------------
STEP 3 – Start Jenkins
------------------------------------------------------------

sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl status jenkins

------------------------------------------------------------
STEP 4 – Unlock Jenkins
------------------------------------------------------------

sudo cat /var/lib/jenkins/secrets/initialAdminPassword

Copy the password and open browser:

http://<server-ip>:8080

Example:
http://192.168.150.129:8080

Install suggested plugins and create admin user.

------------------------------------------------------------
STEP 5 – Install Docker
------------------------------------------------------------

sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

Add jenkins user to docker group:

sudo usermod -aG docker jenkins
sudo systemctl restart jenkins

Verify:

groups jenkins

------------------------------------------------------------
STEP 6 – Create Docker Project Files
------------------------------------------------------------

Dockerfile:

FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html

index.html:

Create an attractive HTML page displaying your name and project details.

------------------------------------------------------------
STEP 7 – Create Jenkinsfile
------------------------------------------------------------

Jenkinsfile defines CI/CD pipeline stages:

- Build Docker image
- Stop old container
- Remove old container
- Run new container

------------------------------------------------------------
STEP 8 – Push Files to GitHub
------------------------------------------------------------

git add .
git commit -m "Added Day4 Jenkins CI/CD files"
git push origin day-4

------------------------------------------------------------
STEP 9 – Configure Jenkins Pipeline
------------------------------------------------------------

Create New Item → Pipeline

Pipeline Configuration:

Repository URL:
https://github.com/soumi04/devops.git

Branch Specifier:
*/day-4

Script Path:
Day4/Jenkinsfile

Save configuration.

------------------------------------------------------------
STEP 10 – Build Pipeline
------------------------------------------------------------

Click Build Now.

Pipeline will automatically:

1. Pull code from GitHub
2. Build Docker image
3. Stop old container
4. Remove old container
5. Run new container

------------------------------------------------------------
STEP 11 – Access Application
------------------------------------------------------------

Open browser:

http://<server-ip>:5000

Example:
http://192.168.150.129:5000

------------------------------------------------------------
FINAL OUTCOME
------------------------------------------------------------

- Jenkins successfully installed
- Docker integrated with Jenkins
- GitHub connected
- CI/CD pipeline automated
- Container deployed automatically
- Website running successfully

------------------------------------------------------------
LEARNING OUTCOME
------------------------------------------------------------

- Jenkins installation and configuration
- GitHub integration with Jenkins
- Docker image lifecycle management
- Container deployment automation
- Understanding of CI/CD workflow

------------------------------------------------------------
📸 OUTPUT SCREENSHOTS
------------------------------------------------------------

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-15 215256.png)

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-15 215528.png)


![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-15 222704.png)


![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-15 225801.png)




# ☁️ DevOps Day 5 – AWS, EC2 & Terraform


- AWS Account Creation
- EC2 Instance Setup (Windows & Ubuntu)
- Terraform Installation
- Terraform Basic Commands
- Implementation Screenshots

---

## 1️⃣ Create AWS Account

1. Go to https://aws.amazon.com  
2. Click Create an AWS Account  
3. Enter Email & Account Name  
4. Verify Email  
5. Set Root Password  
6. Fill Contact Info (Personal)  
7. Add Debit/Credit Card (Free Tier verification)  
8. Complete Identity Verification (OTP)  
9. Choose Basic Support (Free)  
10. Login → Sign In → Root User  

---

## 2️⃣ Create Windows EC2 Instance

- Go to EC2 → Launch Instance  
- Name: Windows-Server  
- AMI: Windows Server 2022  
- Instance Type: t2.micro  
- Create Key Pair (.pem)  
- Allow RDP (3389) and HTTP (80)  
- Launch & Connect using RDP  

---

## 3️⃣ Create Ubuntu EC2 Instance

- Go to EC2 → Launch Instance  
- Name: Ubuntu-Server  
- AMI: Ubuntu 22.04 LTS  
- Instance Type: t2.micro  
- Create Key Pair (.pem)  
- Allow SSH (22) and HTTP (80)  

---

## 4️⃣ Install Terraform (Ubuntu)

Update system:

sudo apt update -y

Install Terraform:

sudo apt install terraform -y

Check version:

terraform -version

---

## 5️⃣ Terraform Basic Commands

Initialize:

terraform init

Validate:

terraform validate

Plan:

terraform plan

Apply:

terraform apply

Destroy:

terraform destroy

---

# 📸 Screenshots

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-15 233610.png)

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-13 144217.png)

![](C:\Users\DELL\Pictures\Screenshots\Screenshot 2026-02-13 151904.png)


---

# ⚙️ DevOps Day 6 – Ansible Apache Deployment

This project demonstrates:

- Ansible Installation on Ubuntu
- SSH Connectivity Testing
- Ansible Inventory Configuration
- Apache Deployment using Ansible Playbook
- Web Server Verification

---

## 1️⃣ Install Ansible on Ubuntu

### Step 1: Update Package List

sudo apt update

### Step 2: Install Ansible

sudo apt install ansible -y

### Step 3: Verify Installation

ansible --version

If installed correctly, the Ansible version details will be displayed.

---

## 2️⃣ Clone Ansible Repository

git clone https://github.com/jagadeeshkanna97/ansible-k.git

cd ansible-k

---

## 3️⃣ Set Key Permission

chmod 400 ubuntudevops.pem

---

## 4️⃣ Test SSH Connection

ssh -i ubuntudevops.pem ubuntu@54.82.36.187

If connected successfully, SSH setup is correct.

---

## 5️⃣ Test Ansible Connectivity

ansible -i inventory.ini slaves -m ping

### Expected Output:

SUCCESS => {
    "ping": "pong"
}

---

## 6️⃣ Run Ansible Playbook (Apache Deployment)

ansible-playbook -i inventory.ini apache-playbook.yml

This will install and configure Apache on the target EC2 instance.

---

## 7️⃣ Verify Apache Service (Inside EC2)

sudo systemctl status apache2

Apache service should be active (running).

---

## 8️⃣ Access Website

Open in browser:

http://54.82.36.187

You should see the Apache default page or deployed web content.

---

---

# 📸 Screenshot

![](https://raw.githubusercontent.com/VARSHINI1805/devops/day-6/Day6/Screenshot%202026-02-14%20120251.png)


---

