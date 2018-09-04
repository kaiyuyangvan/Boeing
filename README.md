# Note:
# This is the draft solution to the assignment
# All jenkins jobs will be setup/run through Jenkins UI or Jenkinscript
# Docker image/container can be generated in Jenkins through Dockerfile

Preparation:
  -hello microservice project source codes and pom.xml file is committed to Git
  -Jenkins server is installed/configured on build server
  -Base docker image has been generated including all necessary components
  -Test/demo/Production server can use AWS/Azure cloud servers or virual boxs or local servers
  -Local server is configured as master jenkins node and test/demo/production severs are confgiured as Jenkins slave nodes

General solution to assignment:
1> Create a Jenkins pipeline job (or generated jenkinscript) to build/unit test micservice application. 
   - tag/snapshoot source code
   - Job will be triggerted by Git post commit hook or "when a change is pushed to GitHub" or Git pull schedule
   - build,unit test and package microservice build artifacts using Maven

2> Create a Jeknins pipeline job to containerize microservice application image
   - Load docker base image on local server
   - copy microservice artifacts to the new docker container
   - Generate docker image with the deployed microservice artifacts
   - The generated docker image has the same name as source code tag
   - The generated docker image is kept in local server or Docker Hub

3> Create a Jenkins pipeline job to deploy microservice to test/demo server
   - Create docker container with current (or selected) version of docker image on test server
   - Run automation test cases (Optional)

4> Create a Jenkins pipeline job to deploy miccroservice to production server  
   - In case of using AWS as production server, 
     Create docker container with current (or selected) version of docker image on production server
     configure load balance setting on AWS server using ansible script, 
   - In case of using visual box or local server as production server, 
     Create mulitple docker containers with current (or selected) version of docker image on production server
     install/configure HAProxy service on production server using ansible script
     


   
   


