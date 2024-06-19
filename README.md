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
mkdir -p "$HOME/.local/share/srv/docker/mailman/rootfs"
git clone "https://github.com/dockermgr/mailman" "$HOME/.local/share/CasjaysDev/dockermgr/mailman"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/mailman/rootfs/." "$HOME/.local/share/srv/docker/mailman/rootfs/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-mailman \
--hostname mailman \
-e TZ=${TIMEZONE:-America/New_York} \
-v "$HOME/.local/share/srv/docker/casjaysdevdocker-mailman/rootfs/data:/data:z" \
-v "$HOME/.local/share/srv/docker/casjaysdevdocker-mailman/rootfs/config:/config:z" \
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
      - "$HOME/.local/share/srv/docker/casjaysdevdocker-mailman/rootfs/data:/data:z"
      - "$HOME/.local/share/srv/docker/casjaysdevdocker-mailman/rootfs/config:/config:z"
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
