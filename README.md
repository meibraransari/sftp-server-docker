---
Created: 2024-07-27T14:01:27+05:30
Updated: 2024-07-31T09:29:24+05:30
Maintainer: Ibrar Ansari
---
<h1 align="center">
  📢📢📢 Attention all Docker 🐳 Beginners & Professionals! 🎯
</h1>

<p align="left">  
    <a href="https://hub.docker.com/r/ibraransaridocker/sftp-server-docker">
        <img alt="SFTP Server Docker" src="https://img.shields.io/docker/pulls/ibraransaridocker/sftp-server-docker" />
    </a>    
</p>

# 💻 Unlock the power of SFTP with this Ubuntu image, perfect for testing and development! 🛠️

## 🚨 Please note: This image is designed for educational and testing purposes 📚 🧪 ONLY! It is NOT SUITABLE for production environments! 🚫

This Docker image is built on Ubuntu 22.04 and comes pre-installed with an SSH server, enabling seamless creation of SSH/SFTP-accessible containers. You can effortlessly configure access using SSH keys or by utilizing a default username and password.

## Step 1: Create Authentication SSH-Keygen Keys.
```
ssh-keygen -t rsa -f ~/.ssh/sftp_id_rsa_key -b 4096 -C "This is used for sftp" -N ""
ls -alsh ~/.ssh/
```
## Step 2: Pull docker image
```
docker pull ibraransaridocker/sftp-server-docker:latest
```
## Step 3: Set variables to run the docker container.
### Change 👇 variables(containername, username, password & port) according to your need.
```
container_name=sftp_server_1
sftp_user=ibrar_ansari
sftp_pass=your_secure_password
sftp_port=2023
container_image=ibraransaridocker/sftp-server-docker:latest
key_path=~/.ssh/sftp_id_rsa_key.pub
sftp_path=/iansari
```
## Step 4: Run docker container.
```
docker run -itd --name=$container_name -p $sftp_port:22 -e SSH_USERNAME=$sftp_user -e PASSWORD=$sftp_pass -e AUTHORIZED_KEYS="$(cat $key_path)" -v $sftp_path:/home/$ssh_user $container_image
```
## Step 5: Test SSH connection 
### Get Node IP:
```
hostname=$(hostname -I | awk '{print $1}')
```

### Pem Key Method:
```
ssh -i ~/.ssh/sftp_id_rsa_key -p $ssh_port $ssh_user@$hostname
```
### Password Method:
```
ssh -p $ssh_port $ssh_user@$hostname
```

## Step 6: Test SFTP Connection 
### Test SFTP connection with password method:
```
sftp <SFTP_USER>@<HOST_IP> -P <PORT>
```
### Test SFTP connection with key method:
```
sftp -P <PORT> -i <PRIVATE_KEY_PATH> <SFTP_USER>@<HOST_IP> 
```
###  # If the -i option is not available, you can use the -o option with a syntax like::
```
sftp -P <PORT> -oIdentityFile=<PRIVATE_KEY_PATH> <SFTP_USER>@<HOST_IP> 
```
### Connection file method:
```
# Create file and assign private key to connect sftp
nano ~/.ssh/config.sftp
Host work
	Host <HOST_IP>
	User <SFTP_USER>
	IdentityFile <PRIVATE_KEY_PATH>
	AddKeysToAgent yes
	Port <PORT>

# Connect it
sftp -F <PRIVATE_KEY_PATH> <HOST_IP>
```

### 💼 Connect with me 👇👇 😊

- 🔥 [**Youtube**](https://www.youtube.com/@DevOpsinAction?sub_confirmation=1)
- ✍ [**Blog**](https://ibraransari.blogspot.com/)
- 💼 [**LinkedIn**](https://www.linkedin.com/in/ansariibrar/)
- 👨‍💻 [**Github**](https://github.com/meibraransari?tab=repositories)
- 💬 [**Telegram**](https://t.me/DevOpsinActionTelegram)
- 🐳 [**Docker**](https://hub.docker.com/u/ibraransaridocker)
