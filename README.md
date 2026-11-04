# rke2 + rancher

## airgapped

https://docs.rke2.io/install/airgap?installation-methods=Binary+install&airgap-load-images=Private+Registry+Method

1. Obtain the images archive for your architecture from the releases page for the version of RKE2 you will be running.
  Assuming amd64, use docker image load -i rke2-images.linux-amd64.tar.zst to import images from the tar file into docker.
- push docker images https://github.com/rancher/rke2/releases/download/v1.36.6-rc2%2Brke2r1/rke2-images.linux-amd64.tar.zst
```
docker image load -i rke2-images.linux-amd64.tar.zst
```

2. Use docker tag and docker push to retag and push the loaded images to your private registry.

3. Follow the Private Registry Configuration guide to create and configure the registries.yaml file.

4. Download the RKE2 binary file rke2.linux-amd64 from the releases page, matching the same version and architecture used to get the airgap images. Place the binary in /usr/local/bin on each air-gapped node and ensure it is executable.

5. Run the binary with the desired parameters. For example, if using the Private Registry Method, your config file would have the following:
```
system-default-registry: "registry.example.com:5000"
```