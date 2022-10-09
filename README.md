# salt-ubuntu-devops-tools

## Windows Users (Only)

Install WSL Preview and Ubuntu 22.04 LTS from the Microsoft Store

* [WSL Preview](https://aka.ms/wslstorepage)
* [Ubuntu 22.04](https://apps.microsoft.com/store/detail/ubuntu-22041-lts)

### Enable Systemd

Launch the Ubuntu distribution, then run the following command to enable SystemD.

```bash
cat <<EOF | sudo tee -a /etc/wsl.conf
[boot]
systemd = true
EOF
```

From a CMD prompt, run the following command to stop the WSL engine.

```bash
wsl --shutdown
```

Relauch the Ubuntu distribution.

## Enable passwordless sudo

Run the following command line to enable passwordless sudo access.

```bash
cat <<EOF | sudo tee /etc/sudoers.d/$(id -un)
$(id -un) ALL=(ALL:ALL) NOPASSWD:ALL
EOF
```

## Install Salt

```bash
sudo apt update -y \
&& sudo apt upgrade -y \
&& sudo apt install -y git salt-minion
```

## Clone this repo

Run the following commands to clone the repository and set appropriate permissions.

```bash
sudo git clone https://github.com/fjudith/salt-ubuntu-devops-tools /srv/salt \
&& sudo chown -R $(id -un) /srv/salt
```
