---
{"dg-publish":true,"permalink":"/software/zerotier-notes/zero-tier-and-github-actions-zero-tier/","tags":["public"],"noteIcon":"1","created":"2023-02-15T16:14:42.812+01:00","updated":"2023-03-07T20:45:39.264+01:00"}
---

#vpn #zerotier #zerotrust #Github 
 ZeroTier is an SDN platform that allows users to create virtual networks that can span multiple devices, locations, and cloud providers. ZeroTier creates an encrypted peer-to-peer mesh overlay that handles NAT traversal and authentication to network resources.
 
 The [ZeroTier Github Action](https://github.com/marketplace/actions/zerotier) allows users to easily integrate ZeroTier into their CI/CD workflows by temporarily connecting runners to a private ZeroTier network.
 
 ```
 - name: ZeroTier
   uses: zerotier/github-action@v1
   with:
     network_id: ${{ secrets.ZEROTIER_NETWORK_ID }}
     auth_token: ${{ secrets.ZEROTIER_CENTRAL_TOKEN }}
 
 - name: ping host
   shell: bash
   run: |
     count=5
     while ! ping -c 1 ${{ secrets.ZEROTIER_HOST_IP }} ; do
       echo "waiting..." ;
       sleep 1 ;
       let count=count-1
     done
     echo "ping success"
 ```
 
 ZeroTier and Github Actions can now be used to securely access internal file servers, package repositories, and container registries, as well as enterprise API endpoints like OpenShift and VMWare.
 
 This action works on the Ubuntu, MacOS and Windows runner types.
 
 After your workflow has completed, it automatically cleans up by revoking the runner’s access to the network.
source: [ZeroTier and Github Actions – ZeroTier](https://www.zerotier.com/2022/12/20/zerotier-and-github-actions/)
