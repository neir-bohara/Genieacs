### Install Docker-CE and Docker Compose (Only for CentOS 7)

```
yum update -y
yum install yum-utils device-mapper-persistent-data lvm2 git -y
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum install docker-ce -y
systemctl start docker
systemctl enable docker

curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose
chmod +x /usr/bin/docker-compose

cd /opt && git clone https://github.com/neir-bohara/Genieacs  && cd Genieacs
```

### Pull/Build Dockerfile

```bash
docker pull neir/genieacs:1.2.0
```
or:
```bash
docker build -f Dockerfile . -t niranjan/genieacs:1.2.0
```

If you decide to build the dockerfile, do not change its name (tag). If you wish to modify it, change docker-compose.yml accordingly.

### Run Docker Compose

**Please**, modify the `docker-compose.yml` file accordingly if you plan to deploy into production. Comment out the `volumes:` directive if you encounter problems in the installation.

If you deploy it in a QNAP's QTS then this is the only step needed after downloading `docker-compose.yml`:

```bash
docker-compose up -d
```

To log into the container, issue the command `docker exec -it genieacs /bin/bash`. If you happen to be managing this setting in your company, better to have some knowledge of Docker.

The UI will be available at port `http://serverip:3000`. You will see a wizard where you can configure GenieACS according to your needs.


