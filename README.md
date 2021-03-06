# Daneel bot

This Node.js app shows how to integrate two ALE ([Alcatel-Lucent Enterprise](https://www.al-enterprise.com/)) tools:
- [**Rainbow**](https://www.openrainbow.com/), the CPaaS platform
- [**OmniVista2500**](https://www.al-enterprise.com/en/products/network-management-security/omnivista-2500-network-management-system), the Network and Identity Management system for LAN (OmniSwitch) and WLAN (OmniAccess)

The aim is showing how easy is to integrate **"Things"** in the new ERA of API Economy. Here, a human with a Rainbow account (freemium model), a bot with Rainbow account, the Rainbow Cloud based CPaaS and OV2500 (Enterprise or Cirrus) will collaborate in order to easy visitor/guest account creation.

This bot will connect with:
- Rainbow SDK for node.js in [**Rainbow API HUB**](https://api.openrainbow.com/#/)
- RESTful API in OV2500

The basic idea is people in a Bubble (Rainbow term for a chat group), can interact with **Daneel Bot**, asking Daneel to create users in OmniVista 2500 (OV2500) UPAM (the Identity Management System), so provisioned users can use SSIDs with 802.1X authentication.

The human interacting with Daneel, can be seen as a **sponsor** asking for credentials for a visitor/guest.

IT Department can allow some Rainbow users in the corporation to have access to Daneel.

The Bot is connected to the Corporate Rainbow space, and IT manager creates a Bublble to include Daneel Bot.

## Interacting with Daneel bot:

Daneel will listen to request coming from sponsors:

- Username: u:username - starts the process... Daneel waits for the password... or will timeout.
  - Example: `u:username1`

- Password: 
  - p:password - manually introduced password
    - Example: `p:password2018`
  - p:w - Daneel will generate a weak password, suited for humans
    - Example: `p:w`
  - p:s - Daneel will generate a strong password, for positronic androids, or paranoid humans...
    - Example: `p:s`

- Cancel Operation: c:
  - Example: `c:`

- Help: h:
  - Example: `h:`
  
  ![Help of Daneel](https://github.com/jarasanz/rainbow-ov2500/blob/master/Help.PNG)

- Delete a user: d:username
  - Example: `d:username1`

## Installation

1. Install or use your favourite Linux distro, I'll be using Ubuntu
2. Install node.js, I would recommend to go LTS or latest, usually Ubuntu repos are not so updated regarding Node.js.
  - Install from binary packages - [Node.js Downloads](https://nodejs.org/en/download/)
  - Install from NodeSource repository - [Node.js Installing from PPA for Ubuntu/Debian](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions)
    * For Current-Latest features (Node.js 9):
    ```bash
    sudo apt-get install curl
    curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
    sudo apt-get install -y nodejs
    ```
  - Check Node.js release:
  ```bash
  nodejs -v
  v9.10.0
  ```
3. I'm not yet providing the package for a complete installation (npm pack), so have to install npm modules by hand:
  - Following the [package.json](https://github.com/jarasanz/rainbow-ov2500/blob/master/package.json), you can find the dependencies:
    - async
    - human-password
    - rainbow-node-sdk
    - request
  - Create a directory in your HOME directory
  ```bash
  mkdir bot
  cd bot
  ```
  - Initializate your Node.js program with npm, keep the name of the main file (index.js)
  ```bash
  npm init
  ```
  - Install node.js modules with npm:
  ```bash
  npm install async --save
  npm human-password --save
  npm rainbow-node-sdk --save
  npm request --save
  ```
  - Download [index.js](https://github.com/jarasanz/rainbow-ov2500/blob/master/index.js). If during ```npm init``` the main name of the js script was changed, rename index.js to that name.
  - Using your favorite editor, edit the index.js file:
    - Change IP address for OV2500, OV2500 username and password
    ```node
    const OV2500 = "192.168.1.10";
    const ovuser = "admin";
    const ovpass = "switch";
    ```
    - Change the Rainbow credentials for your bot:
    ```node
    // Define Rainbow configuration
    let options = {
        "rainbow": {
            "host": "openrainbow.com",     
        },
        "credentials": {
            "login": "bot_user@mail.com", //<--- Bot username here
            "password": "bot_password"    //<--- Bot password here
    ```
  - Start the program
  ```bash
  node index.js
  ```

# 
This program is distributed as is. Use, modify or distribute it, but please mention the author.
