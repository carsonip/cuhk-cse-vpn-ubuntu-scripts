# CUHK CSE VPN Script for Ubuntu 14.04+

## Background

This script was originally written by [@nnkken](https://github.com/nnkken) and is now modified by [@carsonip](https://github.com/carsonip) to reflect the changes in the CUHK CSE VPN systems.

The original scripts are available [here](https://drive.google.com/file/d/0B7OCa-W_RqCzd2UzWFE2WmJZM3M/view).

## Introduction

This script is for connecting to the CSE VPN (to be more accurate, vpn.cse.cuhk.edu.hk) on Ubuntu 14.04.

For the first time connecting to VPN, please run:

```shell
sudo ./install.sh
```

The script will check and install the following packages:

 - strongswan
 - xl2tpd
 - ppp
 - isc-dhcp-client

The script will then help you to set the required config files, and also the CSE ID and password.

For each computer, you need to run the script once only.

To connect to the VPN, please run:

```shell
sudo ./vpn_connect.sh
```

To disconnect from the VPN, please run:

```shell
sudo ./vpn_disconnect.sh
```

## Troubleshooting
The scripts are incompatible to the scripts for connecting to CUHK VPN provided by ITSC.

If you have installed those scripts previously, you may find that you cannot connect to either CUHK VPN or CSE VPN using this script.

In this case, please run

```shell
sudo rm /etc/ipsec.conf
```

and then run install.sh again.

If the scripts fail in step "Connect to the VPN server", or get frozen in step "Change default route to ppp0", please check that you have input the correct password, or simply reinstall the scripts.

If you find that you cannot access to the internet after using the scripts, you may try:

```shell
sudo ip route add default via __GATEWAY__ dev __DEVICE__
```

with __GATEWAY__ and __DEVICE__ be replaced by the gateway and device respectively, which could be found in the step "Get default device and gateway".

## Contributing
If you experience problems, please create an issue. If you have the idea how to fix it, please feel free to fork and submit pull requests.
