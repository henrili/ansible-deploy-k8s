## Creating an auto-install ISO of ubuntu server

The software needed to create an ISO is called cubic. This may be available on other platforms, but I have only tested this on an ubuntu 22.04 desktop VM.

The following commands installs cubic, creates a project directory, downloads the source iso file,
and opens cubic.

```command
sudo apt-add-repository ppa:cubic-wizard/release
sudo apt update && sudo apt install cubic -y
mkdir cubic
wget https://releases.ubuntu.com/22.04.3/ubuntu-22.04.3-live-server-amd64.iso
cubic ./cubic ./ubuntu-22.04.3-live-server-amd64.iso
```