# Docker OpenVPN Transmission

## Pre Requiresites

You must generate OpenVPN configuration files from your VPN provider.

### Install Docker Compose

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

### Create directories

```
mkdir docker-openvpn-transmission
mkdir docker-openvpn-transmission/config
mkdir docker-openvpn-transmission/downloads
```

## Configuration

Put your OpenVPN configuration files in the `config` folder. 

This Docker Compose file suppose that your credentials are in configuration files.

Copy `docker-compose.yml` to the root level of the created folder `docker-openvpn-transmission`.

## Launch the stack

```
docker-compose up -d
```

## Validate

### Get your IP outside the containers stack

``` 
curl api.ipify.org
```

### Get your IP inside the containers stack

```
docker -exec -ti docker-openvpn-transmission_bit_1
curl api.ipify.org
```

You must get a different IP.

## Use

From a browser, type `http://<localhost_or_IP_OF_YOUR_HOST>/transmission/web`.

Default login : `admin:admin`.

You must edit the Transmission configuration to set the download directory at `/downloads`.

Feel free to update `docker-compose.yml` to match with your preferences. 

## Credits

https://hub.docker.com/r/dperson/openvpn-client \
https://hub.docker.com/r/dperson/transmission \
https://hub.docker.com/r/dperson/nginx