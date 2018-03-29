## Docker

Start a linux-based VM or host (Deb/Ubuntu/...)

**Get there for Ubuntu, follow instructions and get to GLPI install**
```
https://docs.docker.com/install/linux/docker-ce/ubuntu/
```

If you're using Debian:

```
sudo apt update
```

Install dependencies
```
sudo apt-get install \
     apt-transport-https \
     ca-certificates \
     curl \
     gnupg2 \
     software-properties-common \
     git
```

Add Docker GPG key
```
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
```

Add Docker repository
```
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
```

Update your apt
```
sudo apt update
```

Install Docker
```
sudo apt install docker docker-ce
```

Install Docker-Compose
```
sudo curl -L https://github.com/docker/compose/releases/download/1.20.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```

Executable permissions to the binary
```
sudo chmod +x /usr/local/bin/docker-compose
```

## GLPI

For GLPI, clone my git repo
```
git clone https://github.com/Griffith3D/SIO.git
```
It will create a folder in your current path

cd to this folder then copy example file
```
cp glpi.sample.env glpi.env
```
And edit glpi.env with your MariaDB configuration

Proceed to next phase : install FusionInventory plugin

## Fusion Inventory

Get FusionInventory plugin :
```
sudo curl -L https://github.com/fusioninventory/fusioninventory-for-glpi/releases/download/glpi9.2%2B2.0-RC1/fusioninventory-9.2.2.0-RC1.tar.bz2 -o fusion.tar.bz2 
```

Unzip it
```
sudo tar xvzf fusion.tar.bz2
```

## Start containers
Once everything is set up, run

```
sudo docker-compose up -d
```

It will create the containers, running in daemon.

Read https://docs.docker.com/compose/ for more commands

## Connect to GLPI HTTP API

If you're running your containers on your host, type 
`http://127.0.0.1:8085`, or if you're running containers on a VM, you can access it by typing the IP address of your VM followed by the port `:8085`

Now, follow the quick connexions steps on your web navigator and FusionInventory should be detected automatically.

