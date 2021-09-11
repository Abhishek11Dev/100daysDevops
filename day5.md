**Docker compose**

Today I take a sample application running from git running with 5 different services 
first I ran application by running all 5 container separately using link command 
the I created docker-compose.yml file and run at once so i get all 5 container started successfully 

steps I followed 

1.clone projects from git 
         git clone https://github.com/dockersamples/example-voting-app.git

2.create images from docker files by going in  respective directory with respective names
        
        docker build . -t vote
        docker build . -t worker
        docker build . -t result

3.run following containers with following order 

          docker run -d --name="redis" redis
          docker conatiner run d -p 5000:80 --link redis:redis vote
          docker run -d -e POSTGRES_HOST_AUTH_METHOD=trust --name="db"  postgres:9.4
          docker run -d --link redis:redis --link db:db worker
          docker container run -d -p 5001:80 --link db:db result

4.Test application on browser

5.remove all conatiner 
    
    docker rm -f $(docker ps -a -q)

6.install docker compose 

7.save following file with docker-compose.yml

                redis:
                    image: redis

                db:
                  image: postgres:9.4
                  environment:
                      - POSTGRES_HOST_AUTH_METHOD=trust

                vote:
                   image: vote
                   ports: 
                      - 5000:80
                   links:
                      - redis

                worker:
                    image: worker
                    links: 
                          - redis
                          - db

                result:
                     image: result
                     ports: 
                         - 5001:80
                     links:
                         - db

8. run docker compose file
 
      docker-compose up
