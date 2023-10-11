# rocket-pool-node-setup

## Linux Installation

Used [this video](https://www.youtube.com/watch?v=P9a0TALERK8&ab_channel=AvoidErrors) as reference for installing Ubuntu 20.04 


## Configuring ssh connection
[Reference Doc](https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-20-04/)
By default when ubuntu is first installed remote access via ssh is not allowed. 

First install `openssh-server` on Node
```shell
sudo apt update && sudo apt install openssh-server
```

Check status of ssh server:
```shell
sudo systemctl status ssh
```

Allow ufw firewall to accept ssh:
```shell
sudo ufw allow ssh
```

Setup Tailscale Virtual Network. Follow [these steps](https://docs.rocketpool.net/guides/node/tailscale.html)


Follow [these steps](https://docs.rocketpool.net/guides/node/securing-your-node.html#essential-enable-automatic-security-updates) in rocketpool docs. Make sure to use ip address setup by Tailscale instead local node network IP address

Note: we did not setup Two-Factor Authentication 
