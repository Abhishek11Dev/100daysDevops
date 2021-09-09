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

code   app.py

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


start web server     FLASK_APP=app.py flask run --host=0.0.0.0

Test    Open a browser and go to URL

http://<IP>:5000                            => Welcome
http://<IP>:5000/how%20are%20you            => I am good, how about you?

    
    
    
  
