FROM amd64/ubuntu:20.04

RUN apt-get update \
    && apt-get install -y systemd \
    && apt-get install -y curl \
    && curl -s -L https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64 --output /usr/bin/jq \
    && chmod +x /usr/bin/jq \
    && DM_STABLE=`curl -s https://kasa.vchasno.ua/api/v2/dm/versions | jq -r '.ver.linux.x64'` \
    && curl -s "https://kasa.vchasno.ua/cloud-cgi/dm-releases/DeviceManager_${DM_STABLE}.deb" --output /usr/src/dm.deb \
#    && (dpkg -i --force-all /usr/src/dm.deb || true) \
    && dpkg -i --force-all /usr/src/dm.deb \
    && apt-get clean \
    && rm -f /usr/bin/jq \
    && rm -rf /var/lib/{apt,dpkg,cache,log}/ \
#    && mkdir -p /usr/share/edm \
    && echo "[Server]\nServerPort=3939\nRemoteAccess=1\nLogsPath=/usr/share/edm/Logs/\nUseHttps=0\nCertFile=\nKeyFile=\nKeyPass=" > /usr/share/edm/EDMSrv.ini \
    && echo "\n\n[Database]\nType=\nServer=\nPort=\nDBName=/var/lib/edm/main.s3db\nLogin=\nPass=" >> /usr/share/edm/EDMSrv.ini

CMD ["/usr/share/edm/EDMSrv"]