# Day-3-Building-a-Secure-Elasticsearch-Deployment

Elasticsearch is a powerful search and analytics engine that enables the fast and scalable search of data. In this tutorial, I’ll walk you through setting up an Elasticsearch instance on a Vultr Cloud server using Ubuntu 22.04.

## Step 1: Create a VPC and Ubuntu Server on Vultr Cloud

### Log into your Vultr Cloud Account:
1. Navigate to the Vultr Cloud dashboard.
2. Create a VPC (Virtual Private Cloud):
   - On the left sidebar, click on **Product** and then select **VPC 2.0**.
   - Choose your preferred location where you want to deploy your VPC.

### Create a New Server:
1. Make sure the VPC 2.0 and the server are in the same location.
2. Click on **Create New Server** in the top right corner of your dashboard.
3. Select **Ubuntu 22.04** as your operating system.
4. For the plan, choose the **80GB NVMe** option.

![Create VPC and Server](INSERT_IMAGE_URL_HERE)

## Step 2: SSH into Your Ubuntu Server and Update Repositories

### SSH into Your Server:
1. Open Windows PowerShell on your local machine.
2. Use the following command to SSH into your server:
   ```bash
   ssh root@your_server_ip_address
