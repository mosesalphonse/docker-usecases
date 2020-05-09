# Few Docker uses cases: Real-life Use Cases, Examples, and Takeaways

* It is interesting that my initial motivation for using Docker is trying out the latest technology.

* Before using Docker, we need to set up separate development environments for different languages. 

* Since Docker is language-agnostic at containment level, which means we can unify the environment and save lot of setup time before kick-starting development. And for software development, saving time is not just about improving your own efficiency; it helps clients save costs too. 

<h2> Here are some simple uses cases along with examples.</h2>
  
  <h3> prerequisite</h3>
  
  * Docker must be installed 
  
    Run the below command (make sure it returns the docker details)
      
      <i>docker info</i>
      
 
  <h3> Adding files(non-jars) into docker images</h3>
 
 a) verify .dockerignore and add the file format(here try to add .json file into docker image) :
  
    !tmp/one.csv

  Note: When you do the docker build, the above files moved into docker image under /tmp/ folder
  
  b) In Docker file add te below

    COPY {file name} /tmp/

     example :

      COPY tmp/one.csv /tmp/
 

  <h3> Copy files into docker running container</h3>
  
  a) Copy files
  
  <b> syntax:</b> 
  
    docker cp {Filename} {container ID}:/tmp

      example :

      docker cp one.csv b07ac8872087:/tmp
      
   b) login into docker container
   
   docker exec -it {container ID} /bin/bash

   example :
   
    docker exec -it b07ac8872087 /bin/bash
    
   c) verify the file inside docker container:
    
    cd /tmp
  
    ls
   
  <h3> Working with Volume</h3>
  
  Create Volume:
  
  Syntax : docker volume create {volume name}
  
  Example:
    
    docker volume create svolume
 
 Inspect Volume:
  
  Syntax : docker volume inspect {volume name}  or docker volume ls
  
  Example:
    
    docker volume inspect svolume
    
    docker volume ls
    
 Remove Volume:
  
  Syntax :  docker volume rm {volume name}  or
            docker system prune
            docker volume prune
  
  Example:
    
    docker volume rm svolume
    
    docker volume ls
    
