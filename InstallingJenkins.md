# Installing Jenkins in Linux and creating a freestyle Nginx project


## Installing JDK 17
```bash
sudo apt install -y openjdk-17-jdk
sudo update-alternatives --config java
```

![1](https://github.com/user-attachments/assets/75ed3b14-c3ee-41e1-b83f-681c6bafd641)

 - After this you'll be prompted to select a java version select the index with java-17

![1](https://github.com/user-attachments/assets/5ca00311-ea4c-44eb-b27c-a4e793ac5752)

## Installing Jenkins
```bash
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

![1](https://github.com/user-attachments/assets/467fc754-01ee-490e-a71e-e14b916494de)

## Starting Jenkins
```bash
sudo systemctl status jenkins
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```
 - Copy the password provided in this step

![1](https://github.com/user-attachments/assets/8f7d48c8-66ac-4d48-b0ef-e420dcbc3b13)

## Jenkins Initial Setup
 - Open a browser and go to `localhost:8080` and paste in the password

![1](https://github.com/user-attachments/assets/23cefbc4-25ca-4ddc-a59c-3c958275764c)

 - Click on `continue`

![1](https://github.com/user-attachments/assets/ea2b865f-689d-4d00-801c-8e4847a20adb)

 - Click on `Install Suggested Plugins`

![1](https://github.com/user-attachments/assets/4fe685f6-5245-4075-ad4c-a87e981c25ca)

 - The plugins will eb installed one by one and you'll be redirected to the next page click `Start Jenkins`

![1](https://github.com/user-attachments/assets/ebd355c3-034e-4fe8-af74-d780d15bf8d7)

 - Fill in your details and create user id and password then click `save and continue`
> [!NOTE]  
> Remember this user id and password. This will overwrite the `Initial Password` generated, and will be required to login everytime you restart Jenkins.

![1](https://github.com/user-attachments/assets/41acee70-682f-4f54-912a-e9756a677091)

 - Leave the default Jenkins URL then click `Save and Finish`

![1](https://github.com/user-attachments/assets/7dc3ae3c-85f4-4820-80a4-9b455affc3ae)


## Setting up a Nginx freestyle project in Jenkins
 - In Jenkins home page click on `create a job`

![1](https://github.com/user-attachments/assets/90d7c7fb-50ed-4bd3-93f4-5afb45a29734)

 - Enter a project name
 - Select `Freestyle Project`
 - Click `Ok`

![1](https://github.com/user-attachments/assets/03d4672d-21e5-467f-9742-035c662784b8)

 - In the next page scroll down to `Build Steps`
 - Click `Add Build Step`
 - Select `Execute Shell`

![1](https://github.com/user-attachments/assets/60f7d6b0-85e9-44eb-a78b-9a94e8d46a94)

 - Paste in the below code
```bash
#!/bin/bash
# Update package lists
sudo apt update -y

# Install Nginx
sudo apt install -y nginx

# Start and enable Nginx
sudo systemctl enable nginx.service
sudo systemctl start nginx

# Verify Nginx is running
systemctl status nginx
```

![1](https://github.com/user-attachments/assets/27fd056c-ea7e-4069-9f23-fd7887260f96)

 - Click `Build Now` in the left side panel
   
![1](https://github.com/user-attachments/assets/290bb3be-cf50-40e8-b42e-a1cc9e2f2341)

 - Your first Nginx project using Jenkins is successfully deployed!
 - Click on the Build in `Builds` and click on the `Console Output` to view the logs
![1](https://github.com/user-attachments/assets/7a1271e1-da3a-4a32-95f0-de143585f826)
