# masscan

Docker image build


[masscan repo](https://github.com/robertdavidgraham/masscan)

[gcr base images](https://console.cloud.google.com/gcr/images/distroless)


### To use this with the provided exclude.conf

```
docker run -it --rm $(IMAGE_NAME) --excludefile /etc/exclude.conf 192.168.69.0/24 -p 80
```
