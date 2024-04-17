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


## Rocket Pool Installation
Follow [these steps](https://github.com/rocket-pool/smartnode-install) to install rocket pool cli

Needed to use these commands:
```shell
sudo curl -L https://github.com/rocket-pool/smartnode-install/releases/latest/download/rocketpool-cli-linux-amd64 --create-dirs -o /usr/local/bin/rocketpool && sudo chmod +x /usr/local/bin/rocketpool
```

## Rocket Pool Configuration
### Holesky Testnet

Used Wizard to configure. Chose Lighthouse for Consensus layer and Buse for Execution Layer.

```shell
network: holesky
client mode: locally managed
execution client setup: besu
consensus client setup: lighthouse
lighthouse grafiti: Anyting4TheMigas

enable checkpoint sync holesky: `https://holesky.beaconstate.ethstaker.cc/`
doppelganger: enabled
metrics: enabled
mev: is disabled on testnet
```

## Swapiness

Default value is set to 60 before we added the following line in `/etc/sysctl.conf` .This sets swapiness to 20 across reboots:

```
vm.swappiness=6
vm.vfs_cache_pressure=10
```

To check current swapiness level:
```
sudo sysctl -p
```

Don't need to reboot after updating swapspace.