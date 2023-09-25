This project is to configure Jenkins master and slave configuration

Pre-requisites
1. download and install Jenkins onto the master node
2. download and install Java onto the master and slave node

Connecting the slave to master:
1. configure the slave node under master
    `-Manage jenkins --> manage nodes and clouds --> New node`
2. Add the node as the permanent agent
3. Provide the below information
   - Name: unique name that identifies the agent
   - Description :
       `> /home/ec2-user/`
Labels: Labels (or tags) group multiple agents into one logical group.
       
4. Usage:
  - Use this node as much as possible
  - Only build jobs with label expressions matching this node

5. Launch method:
  - Launch the agent by connecting it to the master
  - Launch agent via execution of command on the controller
  -`Custom WorkDir path: custom Remoting work directory will be used instead of the Agent Root Directory`
  - Use WebSocket

6. Availability:
  - Keep this agent online as much as possible
  - Bring this agent online according to a schedule
  - Bring this agent online when in demand, and take it offline when idle
Once you save the above configuration you will get a command which should be executed in the agent. it contains agent.jar

7. Errors to look for:
  - Master and slave should have
  - same Java version
  - Same Maven version
  - In case Jave or Maven paths are referring to the agent system then aline it according to masters Global Tool Configuration
  - In the case of the AWS server, make sure your Jenkins URL is updated to the latest Public IP.


  
