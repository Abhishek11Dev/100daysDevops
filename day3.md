**Docker Images**
1. why should we create docker images?

to containerize the application so that you can use docker image to run application / ship application / deploy application 

2.how to create docker image for application / containerizing the application 
   
    a)  start thinking how to deploy application manually 
    
    b)  understand what application we are containerizing , how it works 
        think about it and write down the steps

Example: **Containerizing Python application**

This is a simple web application using Python Flask. This is used in the demonstration of development of Docker image.

**steps to Run Application**

1.Install Python   apt install -y python

2.Install pip      apt-get -y install python3-pip

3.Install flask    pip install flask

code   **app.py**

      import os
      from flask import Flask
      app = Flask(__name__)
      @app.route("/")
      def main():
      return "Welcome!"
      @app.route('/how are you')
      def hello():
      return 'I am good, how about you?'
      if __name__ == "__main__":
      app.run(host="0.0.0.0")


start web server:    FLASK_APP=app.py flask run --host=0.0.0.0

Test:   Open a browser and go to URL

       http://<IP>:5000                            => Welcome
       http://<IP>:5000/how%20are%20you            => I am good, how about you?
       
 **Steps to Containerizing Application**

1. create directory

2. create 2 files inside directory Dockerfile and app.py

        **Dockerfile**
        
        
         FROM ubuntu
         RUN  apt update
         RUN  apt install -y python
         RUN apt-get -y install python3-pip
         RUN pip install flask
         COPY app.py /opt/app.py
         ENTRYPOINT FLASK_APP=/opt/app.py flask run --host=0.0.0.0


3.To build image      
       
       docker build . -t my-python-app

4.verify image by     docker images

5.Run container     docker run container -p 5000:5000 -d my-python-app

6.test it on browser

7.You can also check 

        docker container run -p 5000:5000 -d abhishekdocker99/my-python-app
        
        https://hub.docker.com/repository/docker/abhishekdocker99/my-python-app


      

 
    
    
  
