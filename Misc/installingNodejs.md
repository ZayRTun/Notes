**Home**
- [Home](../index.md)
---
# Installing Nodejs
To install Node.js and npm from the NodeSource repository, follow these steps:

1. Enable the NodeSource repository by running the following curl as a user with sudo privileges:    
    ```bash
    curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
    ```
    The command will add the NodeSource signing key to your system, create an apt sources repository file, install all necessary packages and refresh the apt cache.

    If you need to install another version, for example 12.x, just change setup_10.x with setup_12.x

2. Once the NodeSource repository is enabled, install Node.js and npm by typing:
    ```bash
    sudo apt install nodejs
    ```
    The nodejs package contains both the node and npm binaries.

3. Verify that the Node.js and npm were successfully installed by printing their versions:
    ```bash
    node --version
    v10.16.3
    npm --version
    6.9.0
    ```
