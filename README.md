<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/JohanScheepers/TTN-Node-Map">
    <img src="images/SIGNALOWL.jpg" alt="Logo" width="160" height="80">
  </a>

  <h3 align="center">TTN Node Coverage Map</h3>

  <p align="center">
    Project is aimed to store node GPS points and then display on a map the nodes and gateway connections
    <br />
    <a href="https://github.com/JohanScheepers/TTN-Node-Map"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/JohanScheepers/TTN_Gateway_Node/blob/main/images/gatewayRadius.gif">View Demo</a>
    •
    <a href="https://github.com/JohanScheepers/TTN-Node-Map/issues">Report Bug</a>
    •
    <a href="https://github.com/JohanScheepers/TTN-Node-Map/issues">Request Feature</a>
  </p>
</p>



<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary><h2 style="display: inline-block">Table of Contents</h2></summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li>
	<a href="#usage">Usage</a>
	<ul>
        <li><a href="#date-selection">Date Selection</a></li>
        <li><a href="#demo">Demo</a></li>
        <li><a href="#flow">Flow</a></li>
      </ul>
    </li> 
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
<details open="open">
## About The Project

In this project were are going to save all the uplinks from TTN in the raw format to a MySQL database. From here we will recall the data and display it on a map. The map will display the location of the node, the uplink path and the gateway the node connected to. The node will be colour and the link as to the rssi.


`TTN-Node-Map`


### Built With

* []()Node-Red
* []()node-red-dashboard
* []()node-red-contrib-web-worldmap
* []()node-red-node-mysql
* []()MySQL
</details>



<!-- GETTING STARTED -->
<details open="open">
## Getting Started

To get a local copy up and running follow these simple steps.

### Prerequisites

* Node-Red
  ```sh
  https://nodered.org/docs/getting-started/
  ```

* node-red-dashboard
  ```sh
  https://flows.nodered.org/node/node-red-dashboard
  ```

* node-red-contrib-web-worldmap
  ```sh
  https://flows.nodered.org/node/node-red-contrib-web-worldmap
  ```
  
  * node-red-node-mysql
  ```sh
  https://flows.nodered.org/node/node-red-node-mysql
  ```
    
  * MySQL
  ```sh
  With a little bit of Googling find the installation for your OS
  ```
  
  * MySQL Workbench
  ```sh
  https://dev.mysql.com/downloads/workbench/
  ```

  * The Things Network – Application with GPS nodes connected
  ```sh
  https://www.thethingsnetwork.org/
  ```
</details>

<details open="open">
### Installation


1. Install Node-Red following the relevant getting started guide for your operating system form the official website
   ```sh
   https://nodered.org/docs/getting-started/
   ```
2. Install npm  package node-red-dashboard
   ```sh
   npm install node-red-dashboard
   ```
3. Install npm  node-red-contrib-web-worldmap
   ```sh
   npm install node-red-contrib-web-worldmap
   ```
4. Install npm  node-red-node-mysql
   ```sh
   npm install node-red-node-mysql
   ```
5. Install MySQL Workbench
   ```sh
   https://dev.mysql.com/downloads/workbench/
   ```
 6. Open Workbeanch and follow the instructions on creating a new database and table. Please keep a note of the username and password for the db, we will require it later to set up the node-red flow. We require a table that has two columns, "json" and "timestamp".
   ```sh
   https://dev.mysql.com/doc/workbench/en/wb-getting-started-tutorial-creating-a-model.html
   ```
7. From your application in “The Thing Network” go to your “Console”, select the application that contains your GPS Nodes. This is the application that collect the data from your GPS nodes. 
Go to “Integration” and select “MQTT”, select “Generate new API key”. Note the “Public TLS address”, “Username” and “Password”, this is going to be needed in the MQTT node in the Node-Red flow.

8. Install the Node-Red flow, copping the *.json from below into your Node-Red running on the sever you have installed Node-Red on. “localhost:1880”
   ```sh
   https://github.com/JohanScheepers/TTN_Gateway_Node/blob/master/flow/TTN_Gateway_Radius.json
   ```

9. In the Node-Red flow configure the MQTT node “mqtt from TTN”, here you need the credentials from Step 7 and “MQTT in Node-RED [HowTo]”  the link below is a good resource to read
   ```sh
   https://www.thethingsnetwork.org/forum/t/mqtt-in-node-red-howto/39909
   ```

10. In the Node-Red flow configure the “json to DB” MySQL node. Select in the Database dropdown “Add new MySQLdatabase”. Enter  your Host, Port 3306, User, Password and Database.

11.  In the Node-Red flow configure the “Query date from json BD - Set Date correct format”, here you need to add your database in the msg.topic. Where you see “soiot.json” replace this with your database and table name.
12.  In the Node-Red flow configure “DB to json” here in the Database dropdown you should see tor database, if not Deploy your flow and then re-check and see if it is there and select it.

13. In the Node-Red flow configure the function node “Decoder ****”, in my flow I have two different GPS nodes decoders, as I use both Abbeway and Digital Matters GPS nodes. You need the change the “On Start” to suit your device decoder.
14. Deploy your flow, now you need to wait and get some GPS date into the DB so you have date to recall. This will take some time, dependant on how often your nodes report in.
</details>



<!-- USAGE EXAMPLES -->
<details open="open">
## Usage

There are one user interfacing areas, Date Selection, you select the “date from” to “date to”.

### Date Selection

There the user via the dropdown box the “date from” and the “date to”, selects “SUBMIT”.

Now the flow queries the DB and returns the data and plots on the map. It will plot the location of were the node were, the link path and the gateway connected to. The node and link colour is relative to the rssi.

You will note that sometimes the uplink were received by more than one gateway from the node. Here you will see that from one node location there are multiple links, each link will still be relative to the rssi, but you will only notice a plot with a number for the node. If you select it, all the plotted node points will pop up, by selecting one you will be able to see the uplink rssi and the gateway information.

You will also see all the “raw” data in the table from the DB.
</details>

### Demo
<details open="open">
<img src="images/gatewayRadius.gif" alt="Demo" width="900" height="450">
</details>


### Flow
<details open="open">
<img src="images/flow.png" alt="Demo" width="900" height="450">
</details>


<!-- ROADMAP -->
<details open="open">
## Roadmap

See the [open issues](https://github.com/JohanScheepers/TTN-Node-Map/issues) for a list of proposed features (and known issues).
</details>


<!-- LICENSE -->
<details open="open">
## License

Distributed under the MIT License. See `LICENSE` for more information.
</details>


<!-- CONTACT -->
## Contact


Project Link: [https://github.com/JohanScheepers/ TTN-Node-Map](https://github.com/JohanScheepers/TTN-Node-Map)






<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[forks-shield]: https://img.shields.io/github/forks/JohanScheepers/repo.svg?style=for-the-badge
[forks-url]: https://github.com/JohanScheepers/repo/network/members
[stars-shield]: https://img.shields.io/github/stars/JohanScheepers/repo.svg?style=for-the-badge
[stars-url]:https://github.com/JohanScheepers/TTN_Gateway_Node/stargazers
[issues-shield]: https://img.shields.io/github/issues/JohanScheepers/repo.svg?style=for-the-badge
[issues-url]: https://github.com/JohanScheepers/repo/issues
[license-shield]: https://img.shields.io/github/license/JohanScheepers/repo.svg?style=for-the-badge
[license-url]: https://github.com/JohanScheepers/repo/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/johan-scheepers-6a263514a/
