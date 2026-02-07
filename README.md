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
<img width="1919" height="1024" alt="image" src="https://github.com/user-attachments/assets/261cc84a-8054-48ca-9784-e6671701df1e" />


---

### 2. Connect to Instance
```bash
ssh -i "server1.pem" ec2-user@<public-ip>
```

<img width="1919" height="1010" alt="image" src="https://github.com/user-attachments/assets/56e05da9-3d87-42f6-84f0-5b3085717e32" />

---

### 3. Update System
```bash
sudo yum update -y
<img width="1181" height="509" alt="image" src="https://github.com/user-attachments/assets/8fa59629-deaf-42bf-b62d-b9cf40411a59" />

### 4. Create a New User
```bash
sudo adduser adminuser

---

### 5. Set Password for User
```bash
sudo passwd adminuser
<img width="1388" height="968" alt="image" src="https://github.com/user-attachments/assets/fc051bb6-6ba2-46a6-ba10-0694d70d24a4" />


### 6. Add User to Sudo Group
```bash
sudo usermod -aG wheel adminuser
```
**Explanation:** Adds `adminuser` to the `wheel` group for sudo privileges.
<img width="952" height="596" alt="image" src="https://github.com/user-attachments/assets/ab901e58-d671-4d31-8a5e-ecf3378fb513" />


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



### 9. Set File Permissions
Create a shared directory:
```bash
sudo mkdir /opt/devdata
sudo chown :dev /opt/devdata
sudo chmod 770 /opt/devdata
```

<img width="937" height="464" alt="image" src="https://github.com/user-attachments/assets/2671488d-c088-4630-9b47-9b3a78cd0716" />

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
<img width="959" height="391" alt="image" src="https://github.com/user-attachments/assets/28232b47-3fdc-4bce-9604-97fa2509e283" />


- Test access:
```bash
su - adminuser
touch /opt/devdata/testfile
```

<img width="957" height="610" alt="image" src="https://github.com/user-attachments/assets/f5afd5a7-d430-4dc1-b942-1363142105e3" />

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
