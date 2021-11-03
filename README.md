# Atlassian Sandbox Environment

## Pre-conf
I like to work in Linux OS, special in Debian / Ubuntu / MATE https://ubuntu-mate.org/about/. So when you try this, take note of what OS you have. It can be different issues depending on our type of OS. 
You need admin / sudo right to add this info in your "hosts"-file:

```bash
# Docker Atlassian Sandbox
127.10.0.1   crowd.internal
127.10.10.1  jira.internal
127.10.20.1  confluence.internal
127.10.30.1  bitbucket.internal
127.10.40.1  bamboo.internal
127.20.10.1  pgadmin.internal
127.30.10.1  nodered.internal
127.30.20.1  jupyter.internal
```
If you are't able to edit the "hosts"-file, use the ports..  
But you need the unmark in the docker-compose.xml file.

Application | Url
-----------|----------------------  
crowd | http://localhost:8095
jira | http://localhost:8080
confluence | http://localhost:8090
bitbucket | http://localhost:7990
bitbucket-ssh | ssh://localhost:7999
bamboo | http://localhost:8085
pgadmin | http://localhost:5050
nodered | http://localhost:1880
jupyter | http://localhost:8888

### In the docker-compose.yml:
* Crowd is diabled.
* Standard ports are diabled.

## Startup...
````bash
docker-compose up -d
````
1. Go to: http://pgadmin.internal
2. Connect to Postgres database
3. Create a database for the [application].
4. Goto: http://[application].internal
5. Start setup [application] with the database you had created.

## Easy testing, mockups, setup a dashboard...
Use NodeRed (http://nodered.internal) for mockups of your work / testing.  
For example:  
- Add "palette" for SMTP, so Jira can send mail  
- Add "palette" for Dashboard, and show the status from JVM.  
  (To easy view of JVM: add the jolokia-plugin to the [application].)

## Add testcode in Python
Use Jupyet to code in Python for interact with this applications.
http://jupyter.internal
1. You need to start Jupyter in frontground to get a token in the log.
2. Use this token to create a password
3. restart Jupyter in the background and login with the password.

## Links
Application | Url
-----|---------------
Jolokia | https://marketplace.atlassian.com/apps/1213211/jolokia-monitoring-agent
node-red-contrib-mailin-smtp (SMTP for NodeRed) | https://flows.nodered.org/node/node-red-contrib-mailin-smtp
node-red-dashboard (Dashboard for NodeRed) | https://flows.nodered.org/node/node-red-dashboard
@digitaloak/node-red-contrib-digitaloak-postgresql (Postgres for NodeRed) | https://flows.nodered.org/node/@digitaloak/node-red-contrib-digitaloak-postgresql



## License  
[MIT](https://choosealicense.com/licenses/mit/)
