# Setting Up Elasticsearch on Vultr Cloud with Ubuntu 22.04

Elasticsearch is a powerful search and analytics engine that enables the fast and scalable search of data. This tutorial will guide you through setting up an Elasticsearch instance on a Vultr Cloud server using Ubuntu 22.04.

## Step 1: Create a VPC and Ubuntu Server on Vultr Cloud

1. **Log into Your Vultr Cloud Account:**

   - Navigate to the Vultr Cloud dashboard.

2. **Create a VPC (Virtual Private Cloud):**

   - On the left sidebar, click on **Product** and then select **VPC 2.0**.
   - Choose your preferred location where you want to deploy your VPC.

3. **Create a New Server:**

   - Ensure the VPC 2.0 and the server are in the same location.
   - Click on **Create New Server** in the top right corner of your dashboard.
   - Select **Ubuntu 22.04** as your operating system.
   - For the plan, choose the **80GB NVMe** option.

## Step 2: SSH into Your Ubuntu Server and Update Repositories

1. **SSH into Your Server:**

   - Open Windows PowerShell on your local machine.
   - Use the following command to SSH into your server:
     ```bash
     ssh root@your_server_ip_address
     ```

2. **Update and Upgrade Your Repositories:**

   - Once connected to your server, update and upgrade the repositories using:
     ```bash
     apt-get update && apt-get upgrade -y
     ```

## Step 3: Download and Install Elasticsearch

1. **Download Elasticsearch:**

   - Go to your preferred web browser and search for "Elasticsearch download."
   - Navigate to the official Elasticsearch download page.
   - Change the download option to `deb` for `x86_64`.
   - Right-click on the download link and select **Copy Link Address**.
![Download Elastic Search](https://raw.githubusercontent.com/Virus192/Day-3-Building-a-Secure-Elasticsearch-Deployment/main/images/photo_5960977688871158766_w.jpg)


2. **Download Elasticsearch to Your Server:**

   - Return to your PowerShell window (still connected to your server) and use the `wget` command to download Elasticsearch:
     ```bash
     wget <right-click here to paste the copied link>
     ```

3. **Install Elasticsearch:**

   - Once the download is complete, install Elasticsearch using the `dpkg` command:
     ```bash
     sudo dpkg -i elasticsearch-8.15.0-amd64.deb
     ```

## Step 4: Configure Elasticsearch

1. **Navigate to the Elasticsearch Directory:**

   - Go to the directory where Elasticsearch is installed. This is typically in `/etc/elasticsearch/`.

2. **Edit the Elasticsearch Configuration File:**

   - Open the `elasticsearch.yml` file using a text editor like `nano`:
     ```bash
     nano /etc/elasticsearch/elasticsearch.yml
     ```
   - Find the line with `network.host:` and modify it to your server’s public IP address. Also, ensure that you remove the `#` in front of the `network.host` and `http.port: 9200` lines to uncomment them.

3. **Save and Exit:**

   - After making the necessary changes, save the file and exit the text editor:
     - In `nano`, you can save the file by pressing `CTRL + S`, and then exit by pressing `CTRL + X`.

## Step 5: Enable and Start the Elasticsearch Service

1. **Reload the Daemon:**

   - Reload the systemd manager configuration:
     ```bash
     systemctl daemon-reload
     ```

2. **Enable Elasticsearch Service:**

   - Enable Elasticsearch to start automatically on boot:
     ```bash
     systemctl enable elasticsearch.service
     ```

3. **Start Elasticsearch Service:**

   - Start the Elasticsearch service:
     ```bash
     systemctl start elasticsearch.service
     ```

4. **Check Elasticsearch Service Status:**

   - Verify that the Elasticsearch service is running correctly:
     ```bash
     systemctl status elasticsearch.service
     ```

   - The status should show as `active (running)`.

## Conclusion

You have successfully set up Elasticsearch on your Vultr Cloud server! You can now start using Elasticsearch for your search and analytics needs. Don’t forget to secure your Elasticsearch instance and configure it according to your specific use case.
