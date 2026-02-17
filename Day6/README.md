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
