Installation & configuration
==============================

## Install dependences
1. Install Docker using instructions - https://docs.docker.com/install/
2. Install Docker-compose using instructions - https://docs.docker.com/compose/install/
3. Put your webbapp to 'app/' .
4. Put your 'db-dump.sql' to 'mysql/' and uncomment appropriate string in 'mysql/Dockerfile' if required.
5. Create Nginx vhost-config in 'nginx/confs/' using as an exaple '001-default.conf'.

#### Run environment
	sudo docker-compose up --build
or

	sudo docker-compose up -d --build

You can see or edit port forwarding (local-net. <-> docker-net.) in docker-compose.yml
