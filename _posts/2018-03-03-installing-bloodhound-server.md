---
layout: default
title: "Installing Bloodhound Server"
date: 2018-03-03 12:00:00
tag: How_To
description: "Getting a Bloodhound server running using a Neo4j Docker image"
---

# Background

___

[Bloodhound](https://github.com/BloodHoundAD/Bloodhound) is an Windows Active Directory relationship visualization tool. From the [wiki](https://github.com/BloodHoundAD/Bloodhound/wiki):

> BloodHound uses graph theory to reveal the hidden and often unintended relationships within an Active Directory environment. Attack[er]s can use BloodHound to easily identify highly complex attack paths that would otherwise be impossible to quickly identify. Defenders can use BloodHound to identify and eliminate those same attack paths. Both blue and red teams can use BloodHound to easily gain a deeper understanding of privilege relationships in an Active Directory environment.

BloodHound is developed by [@\_wald0](https://twitter.com/_wald0), [@CptJesus](https://twitter.com/CptJesus), and [@harmj0y](https://twitter.com/harmj0y).

Bloodhound utilizes a [Neo4j](https://neo4j.com/) database to aggregate collected Domain information into an easy-to-understand, feature-rich graphical application. 

<figure>
	<img src="/images/installbloodhound/gui.png" alt="bloodhound-gui-view"/>
	<figcaption>GUI-View of Domain Information</figcaption>
</figure>

Bloodhound allows the user to query the ingested data with questions such as:
- Is the current user a member of any nested group that grants greater privileges?
- From the current user what are all the paths to Domain Admin?
- Where are Domain Admins currently logged in?

# Installing the Bloodhound Server

___

As mentioned before, Bloodhound requires a Neo4j graph database to function; I run my Neo4j instance from a docker container, so this tutorial assumes you will do the same. I will also be using *Docker Toolbox* instead of *Docker Community Edition for Windows*, as I prefer to use Virtualbox over Hyper-V.

1. **Download Docker Toolbox for Windows**

   Download Link: [Docker Toolbox](https://download.docker.com/win/stable/DockerToolbox.exe)  
   Leave the defaults checked in the install wizard including Virtualbox if you do not already have it.

2. **Launch Docker Quickstart Terminal**
   
   This was installed via the install wizard. Launching this program will open a MinGW Terminal and begin setting up Docker. When it is finished, you should see a message similar to: `docker is configured to use the default machine with IP 192.168.99.100`. Keep note of this IP, as this is how you will access your Docker containers.  
   - To ensure a successful install, run `docker run hello-world`
   - You should see the following message: `Hello from Docker!`  
<br>
3. **Pull Neo4j Docker Image**
   
   We will pull this image from the Docker store. In the Quickstart Terminal run:  
   - `docker pull neo4j`  
<br>
4. **Start the Neo4j graph server**
   
   In the Quickstart Terminal run:  
   - `docker run --publish=7474:7474 --publish=7687:7687 --volume=$HOME/neo4j/data:/data neo4j`
   - If this command returns with errors, check that your $HOME variable does not contain spaces. If it does, you will need to provide the absolute path to this command, with the offending bit enclosed in quotes  
   (i.e "Program Files"/.../neo4j/data)  
<br>
5. **Change Graph Server Default Password**

   Access the graph server in a browser using the IP from above  
   - `http://192.168.99.100:7474`
   - Login with `neo4j:neo4j` and it will prompt you to change the password  
<br>
6. **Download Bloodhound Release**

   Download Link: [BH Release](https://github.com/BloodHoundAD/BloodHound/releases)  
   Extract the zip file to a directory of your choosing. (I will assume C:\Users\Test for ease of explanation)

7. **Start the Bloodhound GUI**

   Run the application located at:  
   - `C:\Users\Test\BloodHound-win32-x64\BloodHound.exe`
   - Login with:
     - URL: `bolt://192.168.99.100:7687`
     - Username: `neo4j`
     - Password: `Password from Step 5`
   - You should now be logged into the Neo4j database via the Bloodhound GUI. A blank canvas means things are working correctly.  
<br>
8. **Exit the Application and kill Neo4j instance**
   
   In the Docker Quickstart Terminal run:
   - `docker container ls`
   - Find the ID of your neo4j container, then
   - `docker kill <id>`  
<br>
9. **Dump Neo4j Database Configuration**

   In the Docker Quickstart Terminal run:
   - `docker run --volume=$HOME/neo4j/conf:/conf neo4j dump-config`
   - This outputs a configuration file that you will be able to edit  
<br>
10. **Create a New Graph Database**

    Running the Neo4j container



   


