# Setup

#### Lavalink Server Configuration Guide

To connect your Lavalink server with Wace, follow the steps below:

1. **Obtain Your IP Address:**
   *   Inside the terminal of Lavalink Server, use the command:

       ```yaml
       ip a # For Linux
       ipconfig # For Windows
       ```
   * On Pterodactyl Panel, check the sidebar for your IP:PORT.
2. **Authentication:**
   *   Set your authentication details in the configuration file:

       ```yaml
       NODES:
           - host: "IP" # Don't add the port here.
             secure: false
             auth: "YourPassword"
             name: "YourName"
             port: 2333
             
             # For second/fallback node. (You can multiple nodes)
           - host: "IP"
             secure: false
             auth: "YourPassword"
             name: "YourName"
             port: 2333
       ```
3.  **Multiple Nodes Configuration:**

    * You can configure multiple nodes to ensure your Lavalink server has a fallback. Simply add additional node entries under the `NODES` section.


4.  If you don't know what is your IP & Port of the lavalink server, you probably specified it here:

    Access your `application.yml` file:

    * [Line 34 - Host Setup](https://github.com/krushna06/Lavalink-Server/blob/main/application.yml#L34) If Wace and & Lavalink are on the same server.
    * [Line 152 - Port Configuration](https://github.com/krushna06/Lavalink-Server/blob/main/application.yml#L152)
