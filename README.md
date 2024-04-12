# Docker_Project
Microservices Project with Jenkins and Docker


STEP BY STEP GUIDE FOR DOCKER PROJECT DEPLOYMENT USING JENKINS PIPELINE:

STEP:1 

Create 3 ec2-instances/servers, connect servers and update it with hostnames (manage, worker1, worker2)
Run the below commands in all the 3 servers 
    yum install docker -y
    systemctl start docker
    systemctl status docker

Join a cluster with the servers: {run the command in manager server}
    docker swarm init    
this generates a token, copy and paste that in 2 worker nodes

STEP:2 
 Install and run jenkins {manager node}

STEP:3 

write index.html and Dockerfile. I have attached the files in the repo.
 Write the pipeline code.
  add image and repo. variables   ---> add parameterized variables: image; repo
  add password in global environments which will be in manage jenkins --> system --> global environments. {add name as password and give the value}


  STEP:4 
  Give docker socket permissions to build the images in manage server.
          chmod 777 /var/run/docker.sock
   since the file is modified reload daemon and restart docker.
          systemctl daemon-reload
          systemctl restart docker.service

          ## initial 4 stages will run successfully till here. 
          ## when we try to build (2nd stage) the error pops up for permissions , execute the above commands


STEP:5 
 Write the compose.yml file
    Now execute the entire pipeline.
    Check the docker hub
    Take the public ip's and execute those with the different ports which were given in compose.yml file.


    !!!! end of the project   !!!!!
    
  
