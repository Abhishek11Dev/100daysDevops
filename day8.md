**start learning kubernetes** 

contents

**K8S**

1.what is k8s

2.Architecture of k8s

3.K8s components

4.K8s objects

5.manifest

6.configmap

7.secrets

8.Rolling update

9.service

10.load balancing

11.scale up / scale down

12.etcd

13.K8s cluster on premises 


Before starting K8s we should know about monolithic application and microservices 

**Monolithic Application**

Suppose are building one application RailIndia which manages different services provided by Indian Railways 

In my application three modules are there

1)tkt management
      
      book tkt
      plan journey
      
2)Availability
      
      train status
      pnr status
      Seat availability
      
3)Account
      
      cancel tkt
      history

As monolitic application my project will be 

   -- RailIndia
       
       |-src
          
          |-main
             
             |-java 
                   
                   |-com.RailIndia.tkt_management
                   
                   |-com.RailIndia.Availability
                   
                   |-com.RailIndia.Account

             |-resources

             |- webapp

               |- WEB-INF
               
                  |-web.xml
      
       |-pom.xml
            
       
And we will get one war file for this project  from "mvn clean verify" command


**Advantages Of molithic application**

1. Every developer has idea about whole  project

2. As we get only one war file deployment is easy

3. easy to scale up

**disavantages Of molithic application**

1. Application code and architecture is complex and hard to understand

2. take more time for development

3. it will take long time to build and deploy and start the application

4. release management is difficult

5. continues delivery is hard to achieve
    suppose we have only one error in application whole application is running good so to fix that error we have to make whole application down

patching and upgrade impact the availability of application

6. Scalling is easy but we have to unnecessary scale up whole application but we only need to scale up only one or two functionality 




