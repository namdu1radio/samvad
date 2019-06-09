# samvad
Many-to-Many communication using WebRTC over Raspberry Pi

# Setup Guide

## Setting up client

1. Move to a temporary directory by issuing `cd /tmp` in terminal.
2. Clone this repository by issuing `git clone https://github.com/namdu1radio/samvad.git` command in terminal, internet connection is necessary for this step.
3. Nginx setup,
  * If Nginx is not installed already, install it using `sudo apt-get install nginx`
  * Now create a `conference` directory in Nginx's `www` folder by issuing `sudo mkdir /var/www/html/conference` command in terminal
  * Now enable write permission to this directory by issuing `sudo chown <YOURUSERNAME>:www-data /var/www/html/conference` command in terminal
4. Copy the contents of `/tmp/samvad/client` to `conference` directory by issuing `cp -r /tmp/samvad/client/* /var/www/html/conference/` command in terminal.
5. Open `/var/www/html/conference/index.html` in your favorite text editor and change line number `52` and replace the IP `192.168.1.15` with IP address of your current machine, this can be found by issuing `ifconfig` command in the terminal. Leave everything else including `http` protocol and `443` port unchanged Once you have made the changes, make sure the file is saved.

## Setting up server

1. Install NodeJS in your Raspberry Pi, if it's not already installed, issue following commands in the given sequence
  * `sudo apt-get update`
  * `curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -`
  * `sudo apt-get install -y nodejs`
2. Copy the `/tmp/samvad/server` directory to your home directory by issuing `cp -r /tmp/samvad/server ~/conferenceServer`
3. Change directory in terminal to this directory, by issuing `cd ~/conferenceServer` in terminal.
4. Install the dependency of the server by issuing `npm install` command, internet connection is necessary for this step. The server is ready after this step.

# Launching

## Starting the server
1. Change directory to conferenceServer directory by issuing `cd ~/conferenceServer` in terminal.
2. Start the server by issuing `sudo node app.js --port=443` command in terminal.
3. Minimize the terminal so that the server keeps running in background inside the terminal.

## Accessing the conference webpage

You can open Audio Conference webpage by visiting `http://xxx.xxx.xxx.xxx/conference` in any modern web-browser. Replae `xxx.xxx.xxx.xxx` with the IP of the machine where Nginx and conferenceServer are setup. The accessing device, and the Nginx and Conference server should be all part of same network.