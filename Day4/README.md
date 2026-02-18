# DEVOPS DAY 4 JENKINS CI/CD 

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
http://192.168.117.128:8080

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

![](Day4/Screenshot%202026-02-13%20111709.png)

![](Day4/Screenshot%202026-02-13%20085223.png)


![](Day4/Screenshot%202026-02-13%20112615.png)


![](Day4/Screenshot%202026-02-13%20085508.png)

![](Day4/Screenshot%202026-02-13%20101133.png)

![](Day4/Screenshot%202026-02-13%20101631.png)



END OF DAY 4 PRACTICAL
