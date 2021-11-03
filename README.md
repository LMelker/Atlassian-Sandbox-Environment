# Jira & Confluence Sandbox Environment

## Pre-conf
I like to work in Linux OS, special in Debian / Ubuntu / MATE https://ubuntu-mate.org/about/. So when you try this, take note of what OS you have. It can be different issues depending on our type of OS. 
You need admin / sudo right to add this info in your "hosts"-file:

```bash
# Docker Jira Sandbox
127.10.10.1  jira.internal
127.10.20.1  confluence.internal
127.10.30.1  bitbucket.internal
127.20.10.1  pgadmin.internal
127.30.10.1  nodered.internal
127.30.20.1  jupyter.internal
```
If you are't able to edit the "hosts"-file, use the ports..  
But you need the unmark in the docker-compose.xml file.

App | Url
-----------|----------------------  
jira | http://localhost:8080
confluence | http://localhost:8090
bitbucket | http://bitbucket:7990
bitbucket-ssh | ssh://bitbucket:7999
pgadmin | http://localhost:5050
nodered | http://localhost:1880


## Startup...
````bash
docker-compose up -d
````
- Go to: http://pgadmin.internal
- Connect to Postgres database
- Create a database for Jira and confluence
- Goto: http://jira.internal
- Start setup Jira with the database you had created.
- Goto: http://confluence.internal
- Start setup Confluence with the database you had created.


Use NodeRed (http://nodered.internal) for mockups of your work / testing.  
For example:  
- Add "palette" for SMTP, so Jira can send mail  
- Add "palette" for Dashboard, and show the status from JVM.  
  (To easy view JVM: add jolokia-plugin for Jira.)

## Links
Apps | Url
-----|---------------
Jolokia | https://marketplace.atlassian.com/apps/1213211/jolokia-monitoring-agent
node-red-contrib-mailin-smtp (SMTP for NodeRed) | https://flows.nodered.org/node/node-red-contrib-mailin-smtp
node-red-dashboard (Dashboard for NodeRed) | https://flows.nodered.org/node/node-red-dashboard
@digitaloak/node-red-contrib-digitaloak-postgresql (Postgres for NodeRed) | https://flows.nodered.org/node/@digitaloak/node-red-contrib-digitaloak-postgresql



## License  
[MIT](https://choosealicense.com/licenses/mit/)
