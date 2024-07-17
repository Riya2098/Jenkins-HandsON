Setting up Jenkins on Ubuntu

1. sudo apt update && sudo apt upgrade
2.  sudo apt install openjdk-11-jdk
3. wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add - 
4. sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
5. sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BA31D57EF5975CA
6. sudo apt update
7. sudo apt install jenkins
8. sudo systemctl start jenkins
9. sudo systemctl enable jenkins
10. now we navigate to: http://your-instance-ip:8080


After you login to Jenkins, 
      - Run the command to copy the Jenkins Admin Password - `sudo cat /var/lib/jenkins/secrets/initialAdminPassword`
      - Enter the Administrator password

## Install the Docker Pipeline plugin in Jenkins:

   - Log in to Jenkins.
   - Go to Manage Jenkins > Manage Plugins.
   - In the Available tab, search for "Docker Pipeline".
   - Select the plugin and click the Install button.
   - Restart Jenkins after the plugin is installed.

## Docker Slave Configuration

sudo apt update
sudo apt install docker.io
 
### Grant Jenkins user and Ubuntu user permission to docker deamon.

```
sudo su - 
usermod -aG docker jenkins
usermod -aG docker ubuntu
systemctl restart docker
```

Once you are done with the above steps, it is better to restart Jenkins.

```
http://<ec2-instance-public-ip>:8080/restart
```

The docker agent configuration is now successful.




