# vchasno-kasa-docker



```shell
docker build -t my_dm_build -f ./src/Dockerfile_orig .
docker run -it -p 8055:3939 \
    -w /usr/share/edm \
    -v "$(pwd)/prod/logs:/usr/share/edm/Logs" \
    -v "$(pwd)/prod/db_dir:/var/lib/edm" \
    my_dm_build \
    /usr/share/edm/EDMSrv
```


Pure Ubuntu
```shell
docker run --name ubuntu-kassa -it -p 8055:3939 amd64/ubuntu:20.04 /bin/bash -name ubuntu-kassa
```