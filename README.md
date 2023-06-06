![image](https://github.com/HoangGuruu/DevOps-Jenkins-CICD-with-GitHub-Integration-use-EC2-Ubuntu/assets/111829092/3b4e1136-5c17-40fb-a0f0-7a3a441ef496)
# Link tutorials in this project
## 1. Link github install Jenkins
https://github.com/HoangGuruu/DevOps-Command-Line-Install-Jenkins
### Use this link to learn
https://www.jenkins.io/doc/book/installing/linux/#debianubuntu

# Link youtube

# All script i use in this project

## 1. Create AWS EC2 instance
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
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
```
history
```
### We can also use this tutorial to install Jenkins in Amazon Linux 2 
https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/#launching-an-amazon-ec2-instance
