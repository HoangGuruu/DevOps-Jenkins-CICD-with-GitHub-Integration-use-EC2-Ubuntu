![image](https://github.com/HoangGuruu/DevOps-Jenkins-CICD-with-GitHub-Integration-use-EC2-Ubuntu/assets/111829092/3b4e1136-5c17-40fb-a0f0-7a3a441ef496)
# I. Link [tutorials](https://www.youtube.com/watch?v=nplH3BzKHPk&list=PL16dpeBne9TC6FWqB6kc7a5CiIcS2vXiX&index=54&t=5784s) in this project
## 1. Tool for this project
### EC2 Ubuntu
### Jenkins
### GitHub
### Docker ( Maybe ... in future )
## 2. Link github install Jenkins
https://github.com/HoangGuruu/DevOps-Command-Line-Install-Jenkins
### Use this link to learn
https://www.jenkins.io/doc/book/installing/linux/#debianubuntu
## 3. Link Docker Documentation

## 4. Link youtube

# II. All Script and Step i use in this project

## 1. Create AWS EC2 instance - Ubuntu
- Allow 22, 80 , 443
- Allow 8080 : Jenkins with my IP

## 2. Install Jenkin
```
sudo apt update
```
```
sudo apt install openjdk-11-jre
```
```
java -version
```
```
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee \ /usr/share/keyrings/jenkins-keyring.asc > /dev/null 
```
```
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \ https://pkg.jenkins.io/debian binary/ | sudo tee \ /etc/apt/sources.list.d/jenkins.list > /dev/null
```
```
sudo apt-get update
```
```
sudo apt-get install jenkins
```
```
sudo systemctl enable jenkins
```
```
sudo systemctl start jenkins
```
```
sudo systemctl status jenkins
```
Then check with <ip:8080>
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
Then install Jenkins
```
# See all script
history
```
Create First Admin User
## 3. Use Jenkins 
- Create item freestyle item
- Configure item 
GitHub URL the code for your App
Git URL similar
- Create ssh keygen for github to access to ec2
```
ssh-keygen
cd .ssh
ls
cat id_rsa
cat id_rsa.pub
```
## 4. SSH keys in Github
- Copy the public key , and add this
- Verify
## 5. Keygen in Jenkins
- At the repositories - Credentials - Copy id_rsa in to keygen
- Brach : main
- Sec console output to check
## 6. Work with the app
```
cd /var/lib/jenkins/workspace/<nameofyourapp>
ls
```
- Install anything the app need
```
sudo apt install nodejs
sudo apt install npm
```
```
sudo npm install
```
- Run app
```
node app.js
```
- Open port need in security group , example 8000
- Then check ip:8000 in another tab ( ip will not run if we interrupt node app.js )
## 7. Docker 
```
cd /var/lib/jenkins/workspace/<nameofyourapp>
ls 
# if exist
sudo rm Dockerfile
```
- In stall Docker
```
sudo apt install docker.io
```
```
nano Dockerfile
```
- Then add in Docker file
```
FROM node:12.2.0-alpine
WORDIR app
COPY . .
RUN npm install
EXPOSE 8000
CMD ["node","app.js"]
```
```
sudo usermod -a -G docker $USER
sudo reboot
cd /var/lib/jenkins/workspace/todo-node-app
docker build . -t node-app-todo
```

## 8. Build step in Jenkins - Excute shell
```
docker build . -t node-app-todo
docker run -d -name node-todo-app -p 8000:8000 todo-node-app
```
```
sudo chmode 777 /var/lib/jenkins/workspace/todo-node-app
sudo usermod -a -G docker jenkins
sudo systemctl restart jenkins
# And sign in jenkins
```

## 9. Webhook Github with Jenkins to start build when push code 
- Add ip port in webhook
- Change in config jenkins >> Webhook
- Change in excute shell of jenkins 
```
docker run -d -name node-todo-app -p 8000:8000 todo-node-app1
# to different
```

### We can also use this tutorial to install Jenkins in Amazon Linux 2 
https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/#launching-an-amazon-ec2-instance
## 3. 
