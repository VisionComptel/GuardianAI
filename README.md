# GuardianAI Installation Steps

## 🖥️ WSL Setup

### 1. Check if WSL is installed 
    wsl -l -v
    
#### Expected output:
    Default Distribution: Ubuntu-22.04
    Default Version: 2


### 2. If  Ubuntu-22.04 is not showing then install wsl
     wsl --install


## 📁 Prepare Deployment Files

### 3. Navigate to the Rockwell Software folder on D Drive
        cd /mnt/d/SOFTWARES/ROCKWELL SOFTWARES

### 4. Extract the GuardianAI installer .exe
        7z x 1.04.00-FTA_GuardianAI-DVD.exe -o/mnt/d/GuardianAI/        

### 5. Navigate to the GuardianAI Directory on D Drive
     cd /mnt/d/GuardianAI

### 6. Create The Deployment Folder
     mkdir -p ~/deployment

### 7. Copy project files from Windows(D-drive) to Deployment Folder
     cp -r /mnt/d/GuardianAI/* ~/deployment/

### 8. Verify copy
    dir

#### You should see the following files — this confirms the copy was successful:
       controller-profile-migration.sh  
       guardianai-install.sh     
       guardianai-nats.tar   
       guardianai-reset-password.sh  
       guardianai.tar
       backup-raw-data.sh                                                       
       guardianai-backup.tar          
       guardianai-ml-engine.tar 
       guardianai-redis.tar 
       guardianai-uninstall.sh      
       k8s-pause-3-5.tar

     
## 🔧 Install Dependencies     

### 9. Download latest package lists
     sudo apt update

### 10. Upgrade Installed Packages
     sudo apt upgrade -y


##  🚀 Deploy GuardianAI

### 11. Move to deployment folder
     cd ~/deployment

### 12. Execute the following commands from /home/<user> directory to modify the permission to the installation scripts and enable
execution 

        chown -R vc:vc deployment
        chmod 755 ./deployment/*.sh

### 13. Execute the following command to install the FactoryTalk Analytics GuardianAI application

  - Run the Installation Script
    
  - ⚠️ Important: Replace 12345 with your desired GuardianAI login password before running this command.

          ./guardianai-install.sh -p 12345
   -  The -p flag sets the login password used to access the application after installation.
     

## 🌐 Access the Application

### 14. Find the Hostname 
        hostname -f

### 15. Find Your IP Address(if hostname not found)
    ip addr show eth0

   #### Example output:

    2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1480 qdisc mq state UP group default qlen 1000
    link/ether 00:15:5d:ef:ef:d3 brd ff:ff:ff:ff:ff:ff
    inet 172.28.99.149/20 brd 172.28.111.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::215:5dff:feef:efd3/64 scope link
       valid_lft forever preferred_lft forever

   - Note the inet address (e.g., 172.28.99.149) — this is your local IP.

### 16. Open the Application

#### Navigate to the following URL in your browser(Example):

    http://172.28.99.149

   - You will be presented with the GuardianAI login page. Use the password you set during the installation step (-p argument).   
     
    
    
