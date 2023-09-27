# deploy java application to tomcat server

two ec2 instance: 
   
![Screenshot (196)](https://github.com/HIMA10SHREE/java-maven-ci-cd/assets/52618743/697fc962-c7b8-4da9-81c6-0960eaac7e5d)


to configure tomcat:

```bash
sudo apt update
sudo apt install default-jdk
sudo apt install tomcat9 tomcat9-admin
sudo su
cd /etc/tomcat9
vim tomcatusers.xml
```

since the tomcat server need to get access of user access...we need to first configure it:
![Screenshot (177)](https://github.com/HIMA10SHREE/java-maven-ci-cd/assets/52618743/5331c11a-13ed-4961-84ce-cb7b0ac168a9)

in jenkins server :
install : maven
         
          git
          
          docker
          
          jfrog


configure the pipeline:

1.add the tomcat server credentials
2.jfrog credentials
3. install the artifactory plugins
4.deploy to container plugin
5. to go the system configuration page and configure :
   maven and jfrog
          
![Screenshot (181)](https://github.com/HIMA10SHREE/java-maven-ci-cd/assets/52618743/79675745-6345-4b67-b803-155992d20410)
![Screenshot (188)](https://github.com/HIMA10SHREE/java-maven-ci-cd/assets/52618743/ba7e3bb5-db4a-4e36-98cb-37dd232bf722)


6. run the pipeline

![Screenshot (191)](https://github.com/HIMA10SHREE/java-maven-ci-cd/assets/52618743/b8f89172-4a09-41ae-b77a-9a06263d4b6e)

you can see the build .war file inside targets

![Screenshot (184)](https://github.com/HIMA10SHREE/java-maven-ci-cd/assets/52618743/dddb3708-9028-40d7-b0b7-be2f05b37f2d)

now go inside the target folder and write the command:

```bash
curl -X PUT -u admin -T 01-maven-web-app.war http://54.242.103.162:8082/artifactory/example-repo-local/
```
![Screenshot (193)](https://github.com/HIMA10SHREE/java-maven-ci-cd/assets/52618743/d982cd19-1b26-45e8-a9e1-cd68d9d46080)

![Screenshot (190)](https://github.com/HIMA10SHREE/java-maven-ci-cd/assets/52618743/4090c6ea-c5b6-4dd3-b415-d683a48fa7bc)

go to the tomcat server :you can see HIMA_TEST:

![Screenshot (186)](https://github.com/HIMA10SHREE/java-maven-ci-cd/assets/52618743/43a5fd9f-6f38-4d58-85c2-3cfa1cf93f30)

![Screenshot (187)](https://github.com/HIMA10SHREE/java-maven-ci-cd/assets/52618743/eecf5575-204c-4743-a1ac-d008ada60364)

