---
{"dg-publish":true,"permalink":"/programmering/github-actions-container-image-publish/","tags":["public","github","docker"],"noteIcon":"1"}
---

### about 
Github container registry is a good way to publish you docker/container images.
The best way to do this is to use github actions to build you images automagically when pushed to git. Below is a simple example of how you can accomplish this.

### example
```yml
name: CI for releases

on:
  push:
    branches:
      - main

jobs:

  build-and-push-docker-image:
    runs-on: ubuntu-latest
    steps:
      - 
        name: Checkout
        uses: actions/checkout@v2
      -
        name: Set up QEMU
        uses: docker/setup-qemu-action@v1
      -
        name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v1
      -
        name: Login to GitHub Container Registry
        uses: docker/login-action@v1 
        with:
          registry: ghcr.io
          username: ${{ github.repository_owner }}
          password: ${{ secrets.GITHUB_TOKEN }}
      -
        name: Build and push
        uses: docker/build-push-action@v2
        with:
          context: .
          file: ./Dockerfile
          platforms: linux/amd64
          push: true
          tags: ghcr.io/1ARdotNO/imagename:latest
```

> [!INFO] Replace "imagename" and 1ARdotNO based upon owner/rg and desired imagename


### Troubleshooting
Also, if you get error "failed to push ghcr.io unexpected status 403 forbidden"
go to Settings > Actions > General for your repo, and ensure workflow permission is set to **Read and write** 
![attachments/Pasted image 20230404144932.png](/img/user/Programmering/attachments/Pasted%20image%2020230404144932.png)