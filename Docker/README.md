## Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?

```
# たぶん Docker サービスが起動してない
service start docke
or
systemctl start docker
```
