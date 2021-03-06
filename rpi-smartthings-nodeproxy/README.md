# Docker Compose

Use `docker-compose` to execute one or more SmartThings Node Proxy containers.

Edit the `docker-compose.yml` file and update as necessary. Repeat the service block to run multiple containers, for instance for multiple STNP plugins (adjust the port mapping as appropriate!)

## Install Docker on Raspian Jessie

```
echo "deb [arch=armhf] https://apt.dockerproject.org/repo raspbian-jessie main" \
| sudo tee /etc/apt/sources.list.d/docker.list
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install docker-engine
```

Optionally, you can add the `pi` user to the `docker` group and avoid having to `sudo docker` commands.

## Install Docker Compose

On the Raspberry Pi running Raspian,

```
sudo apt-get install python2.7 python-pip
sudo pip install docker-compose
```

## Edit the `docker-compose.yml`

Some fields you may want to update:

* Environment: specify the name of the STNP plugin you want to run in the container.
* Volumes: specify the path to the `config.json` the container should use.
* Devices: specify the name of the USB serial device on the host to grant to the container.

You can repeat the entire service block to run multiple copies of the container, for instance for additional plugins.

## Bring up the services

Execute `docker-compose up -d` to start the services in the background.

Execute `docker-compose down` to shut them down.

