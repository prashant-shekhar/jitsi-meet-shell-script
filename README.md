# jitsi-meet-shell-script

#!/bin/bash
sudo apt install docker-compose
git clone https://github.com/jitsi/docker-jitsi-meet
cd docker-jitsi-meet
cp env.example .env
./gen-passwords.sh

echo "HTTP_PORT=80" >> .env
echo "HTTPS_PORT=443" >> .env
echo "TZ=Asia/Kolkata" >> .env
echo "PUBLIC_URL='https://www.meetelitmus.com'" >> .env
echo "DOCKER_HOST_ADDRESS=192.168.1.0" >> .env
echo "ENABLE_HTTP_REDIRECT=1" >> .env

mkdir -p ~/.jitsi-meet-cfg/{web/letsencrypt,transcripts,prosody/config,prosody/prosody-plugins-custom,jicofo,jvb,jigasi,jibri}


sudo docker-compose up -d
