# Linode-NodeApp

A tutorial showing how to setup a Node.js application in Linode (Debian 12 server). 


## Setup

Create a Linode (https://www.linode.com/) Debian 12 server

Login to Linode with your user account. Choose to create a Linode 


Debian cmd switch `-y` auto confirms 
Login using ssh and the password

```bash
ssh root@172.232.157.64
```

Check your current folder in Debian

```bash
pwd
```

Update and upgrade system

```bash
apt-get update -y
apt-get upgrade -y
```

Install Node.js

```bash
apt-get install nodejs -y
nodejs --version
```
<!-- 18 -->

Install Node Packet Manager npm 

```bash
apt-get install npm -y
npm --version
```
<!-- 9 -->

Create an application folder

<!-- create node app -->
```bash
mkdir nodeapp
cd nodeapp
```

Transfer files from the application using FileZila.

Setup application, and check if it's running

```bash
npm install
npm run dev
```

Terminate application, and install net tools - useful for checking application / troubleshooting.

```bash
apt-get install net-tools -y
```

Edit files in remote Debian environment using cmd `nano [filername]`

```bash
nano server.js
```


Check if application is running on port

```bash
netstat -antup | grep 8081
```

Use `curl` to request page

```bash 
curl http://127.0.0.1:8081
```

If public folder exists (express static folder), an existsing `index.html` file should show up, otherwise an error page 
<!-- folder public, scripts -->

The client side script uses websockets. The servers IP adress and port must match. Creating a Linode server instance will give you an IP adress, like this:

```js
const url = "172.232.157.64"; 
const port = 8081;

// skapa en websocket i klienten
const websocket = new WebSocket(`ws://${url}:${port}`);
```



Use a browser to navigate to teg´h server IP adress, ie 'http://172.232.157.64:8081/'

