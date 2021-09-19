# blue-green
Aws Blue green deployement

# Aws Codedeploy-agent installation on ubuntu 20.04
apt-get update -y
apt-get install -y ruby
wget https://aws-codedeploy-us-east-1.s3.amazonaws.com/releases/codedeploy-agent_1.0-1.1597_all.deb
mkdir codedeploy-agent_1.0-1.1597_ubuntu20
dpkg-deb -R codedeploy-agent_1.0-1.1597_all.deb codedeploy-agent_1.0-1.1597_ubuntu20
sed 's/2.0/2.7/' -i ./codedeploy-agent_1.0-1.1597_ubuntu20/DEBIAN/control
dpkg-deb -b codedeploy-agent_1.0-1.1597_ubuntu20
dpkg -i codedeploy-agent_1.0-1.1597_ubuntu20.deb
systemctl start codedeploy-agent
systemctl enable codedeploy-agent


# Aws codedeploy-agent installation script

#!/bin/bash
sudo apt-get update -y
sudo apt upgrade -y
sudo apt install apache2 -y
sudo systemctl enable apache2
sudo rm rf /var/www/html/*
sudo apt-get install ruby -y
sudo apt-get install wget -y
cd /home/ubuntu
wget https://aws-codedeploy-ap-south-1.s3.ap-south-1.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto
sudo service codedeploy-agent start
sudo systemctl enable codedeploy-agent
