# Contributing

## Build and deploy

```bash
rockcraft pack -v
sudo skopeo --insecure-policy copy oci-archive:./openfga_1.3.9_amd64.rock docker-daemon:openfga:latest
docker run openfga:latest
```
