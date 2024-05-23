# BacnetApiServer


Introduction
--

BacnetAPIServer is an open-source tool that bridges the gap between REST APIs and BACnet systems. It seamlessly translates API calls into BACnet objects, making them readily available for building automation control. Designed to integrate with NodeRED, BacnetAPIServer simplifies the conversion of NodeRED logic into BACnet Objects, streamlining BACnet integration for developers.

Requirements
--

**Compatible Operating Systems:**
 
 Ubuntu
 
 Raspberry Pi OS
 
**Tools:**

Java 1.8 or higher

Node.js 20.11.1


How to Install Java and Node.js
--

**Java Installation**

     sudo apt install default-jdk

**Node.js Installation**

      sudo apt update

      sudo apt install curl 
     
      curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash 
     
      source ~/.bashrc   
     
      nvm install "20.11.1"

 
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

   
      Use any text edit to create the bacnetAPIServer.service

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
             ExecStart=/opt/BacApiServer-0.0.11/bin/startServer.sh
             
             [Install]
             WantedBy=multi-user.target


            sudo systemctl daemon-reload


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
~                          


     
   





 
Download Link
--
https://drive.google.com/file/d/1Vg6xusan1ztSH0ts45toZBwSYi06rCPH/view?usp=sharing

