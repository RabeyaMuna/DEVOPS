# Create a Azure VM using Virtual Machine

1. Select Virtual Machine and select options 
   -
   -

2. Create Public IP address using Virtual Network
   -
   -

3. Access to Azure VM using Public IP address and password

   ```
    ssh username@ip-address
    Enter your password when prompted
   ```

4. Setup Azure VM based on the application requirements.
   - Setup Docker for Azure VM
   ```
    sudo apt update
    sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu  $(lsb_release -cs)  stable"
    sudo apt update
    sudo apt-get install docker-ce
    sudo systemctl start docker
    sudo systemctl enable docker
    sudo systemctl status docker

    sudo groupadd docker
    sudo usermod -aG docker ubuntu
    su - ubuntu
    ```

   - Setup Ngnix for Azure VM

    ```
    sudo apt-get -y update
    sudo apt-get -y install nginx
    sudo systemctl status nginx

    ```
    - If you can't access it from browser right now because we haven't added port rule. To access the server we need to add PORT to Access Rule to our VM. In order to add rule for port, we need to add port in network settings of Azure VM in Add Inbound Port Rule 
    bash ```
    Add Inbound Port Rule

    You need to all expose port in which you want to run the application
    ```

    - SSL Certificate using Certbot

       * add one last PORT 443 rule. As we know HTTPS runs on port 443 and without 443 access browser can't use https connection.

       * Install Certbot in VM

       ```
        sudo apt-get install software-properties-common
        sudo add-apt-repository ppa:certbot/certbot
        sudo apt-get update
        sudo apt-get install python-certbot-nginx
        sudo certbot --nginx
       ```
