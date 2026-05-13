## 👋 Welcome to mailman 🚀  

mailman README  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update mailman
```
  
## Install and run container
  
```shell
dockerHome="/var/lib/srv/$USER/docker/casjaysdevdocker/mailman/mailman/latest/rootfs"
mkdir -p "/var/lib/srv/$USER/docker/mailman/rootfs"
git clone "https://github.com/dockermgr/mailman" "$HOME/.local/share/CasjaysDev/dockermgr/mailman"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/mailman/rootfs/." "$dockerHome/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-mailman-latest \
--hostname mailman \
-e TZ=${TIMEZONE:-America/New_York} \
-v "$dockerHome/data:/data:z" \
-v "$dockerHome/config:/config:z" \
-p 80:80 \
casjaysdevdocker/mailman:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/mailman
    container_name: casjaysdevdocker-mailman
    environment:
      - TZ=America/New_York
      - HOSTNAME=mailman
    volumes:
      - "/var/lib/srv/$USER/docker/casjaysdevdocker/mailman/mailman/latest/rootfs/data:/data:z"
      - "/var/lib/srv/$USER/docker/casjaysdevdocker/mailman/mailman/latest/rootfs/config:/config:z"
    ports:
      - 80:80
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/mailman
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/mailman" "$HOME/Projects/github/casjaysdevdocker/mailman"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/mailman"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
