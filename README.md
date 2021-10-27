<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/JohanScheepers/TTN-Mapper">
    <img src="images/SIGNALOWL.jpg" alt="Logo" width="160" height="80">
  </a>

  <h3 align="center">TTN Gateway Radius and New Node</h3>

  <p align="center">
    Project is aimed to use the TTN API to plot gateways and location of potencial new node on map
    <br />
    <a href="https://github.com/JohanScheepers/TTN-Mapper"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/JohanScheepers/TTN_Gateway_Node/blob/main/images/gatewayRadius.gif">View Demo</a>
    ·
    <a href="https://github.com/JohanScheepers/TTN-Mapper/issues">Report Bug</a>
    ·
    <a href="https://github.com/JohanScheepers/TTN-Mapper/issues">Request Feature</a>
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
## About The Project

In this project were are going to save all the uplinks from TTN in the raw format to a MySQL database. From here we will recall the data and display it on a map. The map will display the location of the node, the uplink path and the gateway the node connected to. The node will be colour and the link as to the rssi.



`TTN-Mapper`


### Built With

* []()Node-Red
* []()node-red-dashboard
* []()node-red-contrib-web-worldmap




<!-- GETTING STARTED -->
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
4. Install the Node-Red flow
   ```sh
   https://github.com/JohanScheepers/TTN_Gateway_Node/blob/master/flow/TTN_Gateway_Radius.json
   ```





<!-- USAGE EXAMPLES -->
## Usage

There are one user interfacing areas, Date Selection, you select the “date from” to “date to”.

### Date Selection

There the user via the dropdown box the “date from” and the “date to”, selects “SUBMIT”.

Now the flow queries the DB and returns the data and plots on the map. It will plot the location of were the node were, the link path and the gateway connected to. The node and link colour is relative to the rssi.

You will note that sometimes the uplink were received by more than one gateway from the node. Here you will see that from one node location there are multiple links, each link will still be relative to the rssi, but you will only notice a plot with a number for the node. If you select it, all the ploted node poits will pop up, by selecting one you will bee able to see the uplink rssi and the gateway information.


### Demo
 
<img src="images/gatewayRadius.gif" alt="Demo" width="900" height="450">


### Flow

<img src="images/flow.png" alt="Demo" width="900" height="450">




<!-- ROADMAP -->
## Roadmap

See the [open issues](https://github.com/JohanScheepers/TTN_Gateway_Node/issues) for a list of proposed features (and known issues).



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.



<!-- CONTACT -->
## Contact


Project Link: [https://github.com/JohanScheepers/ TTN_Gateway_Node](https://github.com/JohanScheepers/TTN_Gateway_Node)






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
