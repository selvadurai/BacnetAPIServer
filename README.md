# BacnetApiServer


Introduction
--

BacnetAPIServer is an open-source tool that bridges the gap between REST APIs and BACnet systems. It seamlessly translates API calls into BACnet objects, making them readily available for building automation control. Designed to integrate with NodeRED, BacnetAPIServer simplifies the conversion of NodeRED logic into BACnet Objects, streamlining BACnet integration for developers.


![image](https://github.com/selvadurai/BacnetAPIServer/assets/4705770/47bc5d81-6fa4-42bf-88e5-fc0ca2b1955b)



Download Link
--
BacApiServer-0.0.11.zip

https://drive.google.com/file/d/1V-In7nlw6GGJLJT-UecnDE5Iok7yl8cu/view?usp=sharing




Requirements
--

**Compatible Operating Systems:**
 
 Ubuntu
 
 Raspberry Pi OS
 
**Tools:**

Java 1.8 or higher

Node.js 20.11.1


How to Install Java,Node.js and NodeRed
--

**Java Installation**

     sudo apt install default-jdk

**Node.js Installation**

      sudo apt update

      sudo apt install curl 
     
      curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash 
     
      source ~/.bashrc   
     
      nvm install "20.11.1"

 **NodeRED Installation**     

 https://nodered.org/docs/getting-started/raspberrypi     


**Credentials for BacnetWeb Portal**

  Default username:admin and password:admin
 
 
Installation Instructions
--
1. Download BacnetAPI Server from the Download Link

2. Put the "BacAPIServer<version>.zip" file in the /opt directory

     command example:
   
       sudo mv BacApiServer-0.0.11.zip /opt/BacApiServer-0.0.11.zip

    File must listed in the opt directory when you type the following command

        ls /opt
   ![image](https://github.com/selvadurai/BacnetAPIServer/assets/4705770/a51112df-06f4-4c17-a681-f2fa7daa0257)
            
3. Go to /Opt directory

    command example:
   
          cd /opt
   
     
4. Unzip  "BacAPIServer<version>.zip"

   command example:

          sudo unzip BacApiServer-0.0.11.zip

5. Creating System D Service

   
      Use any text edit to create the bacnetAPIServer.service and bacnetWebAPIPortal.service

       1). Create bacnetAPIServer.service

             Command example
         
                     sudo vim /etc/systemd/system/bacnetAPIServer.service
   
          
              bacnetAPIServer.service
   
                     [Unit]
                     Description=Bacnet API Backend Server
                     After=network.target
                     StartLimitIntervalSec=0
                     [Service]
                     Type=simple
                     Restart=always
                     RestartSec=1
                     ExecStart=bash /opt/BacApiServer-0.0.11/bin/startServer.sh
                     
                     [Install]
                     WantedBy=multi-user.target

      2). Create bacnetWebAPIPortal.service

           Command Example
        
                     sudo vim /etc/systemd/system/bacnetWebAPIPortal.service
        
           bacnetWebAPIPortal.service
          
                     [Unit]
                     Description=Bacnet API Web Portal
                     After=network.target
                     StartLimitIntervalSec=0
                     [Service]
                     Type=simple
                     Restart=always
                     RestartSec=1
                     ExecStart=bash /opt/BacApiServer-0.0.11/bin/startPortal.sh
                                 
                     [Install]
                     WantedBy=multi-user.target
                                
  
  6. Restart Services
  
           sudo systemctl daemon-reload


  7. Start  bacnetAPIServer.service and  bacnetWebAPIPortal.service

     Command to start bacnetAPIServer.service
     
         sudo systemctl start bacnetAPIServer.service

     Command to start bacnetWebAPIPortal.service
     
         sudo systemctl start bacnetWebAPIPortal.service

 8.Open the following ports

    1.)7007

       sudo ufw allow  7007

   
    2.) 1880

      sudo ufw allow  1880

   
    3.) 3000

      sudo ufw allow  3000

 10. Type <ip_address>:3000 or localhost:3000(Only Applies if your on the server) in your browser. The bacnetAPI Web Portal will Appear

     ![image](https://github.com/selvadurai/BacnetAPIServer/assets/4705770/d9a731a9-b259-46d4-b32b-c0abfebfe404)

         
User Guide
--   
  https://github.com/selvadurai/BacnetAPIServer/tree/main/UserGuide
  
How to Create Bacnet Service in a nutshell:
--
![image](https://github.com/selvadurai/BacnetAPIServer/assets/4705770/fba1caef-b5d3-45bf-8072-50b5812a86ab)

BacnetWebPortal Screenshots:
--
![image](https://github.com/selvadurai/BacnetAPIServer/assets/4705770/841dc1ae-c24a-4151-a306-7f9ca91af312)



![image](https://github.com/selvadurai/BacnetAPIServer/assets/4705770/dee77390-24e2-4727-bc6b-bb3c72907421)


![image](https://github.com/selvadurai/BacnetAPIServer/assets/4705770/bb6f5910-3478-4cc4-8ae2-1e8952febde6)


![image](https://github.com/selvadurai/BacnetAPIServer/assets/4705770/9c61fa14-674c-4e1f-885a-2c066b140aa0)



Developer Resources:
--
BacnetAPIServer leverages Java for its backend, utilizing the Javalin and Bacnet4J libraries. The frontend, known as BacnetWebPortal, is built with Vue.js

BacnetAPIServer:

https://github.com/selvadurai/BacnetServerAPI

BacnetWebPortal:

https://github.com/selvadurai/BacnetWebPortal


