today I learn about how docker images built in layered architecture
docker images are read only but when we run container one read write layer is created on top of docker image
This layer is not permanent , when we stop container this layer disappear and data get lost 

So for persistant storage we create volume
      docker volume create  data-volume 
data-volume dir created inside /var/lib/docker

we can bind directory to docker container
       docker run -v data-volume:/var/lib/mysql mysql

we can use mount command also
          docker --mount type=bind source:/data/mysqlvolume  target:/var/lib/mysql mysql
          
we can check memory aslo 
  docker system df
  docker system df -v
