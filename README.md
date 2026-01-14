# Linux User Management and Permissions on Amazon Linux EC2

## 📌 Project Overview
This project demonstrates Linux administration skills by creating and managing users, assigning permissions, and configuring sudo privileges on an Amazon Linux EC2 instance.

---

## ✅ Prerequisites
- AWS account
- EC2 instance (Amazon Linux 2)
- SSH key pair named `server1`

---

## 🚀 Steps

### 1. Launch EC2 Instance
- AMI: Amazon Linux 2
- Instance type: t2.micro
- Security Group: Allow SSH (22)

**Screenshot:**
images/ec2-launch.png

---

### 2. Connect to Instance
```bash
ssh -i "server1.pem" ec2-user@<public-ip>
```

**Screenshot:**
images/ssh-connect.png

---

### 3. Update System
```bash
sudo yum update -y
```

---

### 4. Create a New User
```bash
sudo adduser adminuser
```

**Screenshot:**
images/user-create.png

---

### 5. Set Password for User
```bash
sudo passwd adminuser
```

---

### 6. Add User to Sudo Group
```bash
sudo usermod -aG wheel adminuser
```
**Explanation:** Adds `adminuser` to the `wheel` group for sudo privileges.

**Screenshot:**
images/user-wheel.png

---

### 7. Verify Sudo Access
Switch to the new user:
```bash
su - adminuser
```
Run a sudo command:
```bash
sudo yum update -y
```

---

### 8. Create a Group and Add Users
```bash
sudo groupadd dev
sudo usermod -aG dev adminuser
```

**Screenshot:**
images/group-dev.png

---

### 9. Set File Permissions
Create a shared directory:
```bash
sudo mkdir /opt/devdata
sudo chown :dev /opt/devdata
sudo chmod 770 /opt/devdata
```

---

### 10. Verify Permissions
- Check directory permissions:
```bash
ls -ld /opt/devdata
```
Expected output:
```
drwxrwx--- 2 root dev 4096 Nov 18 18:00 /opt/devdata
```

- Check user groups:
```bash
groups adminuser
```
Expected output:
```
adminuser : adminuser wheel dev
```

- Test access:
```bash
su - adminuser
touch /opt/devdata/testfile
```

**Screenshot:**
images/permissions.png

---

## 🔑 Key Linux Commands Used
- `adduser`, `passwd`, `usermod`, `groupadd`
- `chmod`, `chown`
- `su`, `sudo`

---

## ✅ Future Enhancements
- Configure SSH key-based login for new users.
- Implement audit logging for user activities.

---

## 🎯 Why This Project?
- Demonstrates Linux user and group management.
- Shows permission handling and sudo configuration.
- Perfect for showcasing Linux admin skills on your CV.
