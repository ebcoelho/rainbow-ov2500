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

- Username: u:<username>, starts the process... Daneel waits for the password... or will timeout.
  - Example: `u:username1`

- Password: 
  - p:<password>, manually introduced password
    - Example: `p:password2018`
  - p:w , Daneel will generate a weak password, suited for humans
    - Example: `p:w`
  - p:s , Daneel will generate a strong password, for positronic androids, or paranoid humans...
    - Example: `p:s`

- Cancel Operation: c:
  - Example: `c:`

- Help: h:
  - Example: `h:`

- Delete a user: d:<username>
  - Example: `d:username1`

The program use Rainbow Node.js SDK and OV2500 RESTful API.

This program is distributed as is. Use it, modify or distribute, but please mention the author.
