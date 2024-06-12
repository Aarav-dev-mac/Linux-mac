# Linux-mac
Linux Mac OS for termux installation link provided in readme and also details

This project provides a script to set up a MacOS-like Debian environment on Termux. The script downloads a pre-configured Debian environment and synchronizes it with the existing installation without deleting any files.

## Features

- MacOS-like interface for Debian in Termux
- Easy setup script
- Ensures existing files are not deleted during synchronization

## Installation

apt update && apt upgrade -y

pkg install -y megatools wget proot-distro rsync

proot-distro install debian

DOWNLOAD_URL="https://mega.nz/file/Fa0DjSAb#3bWB5YK9H7ztBK8wLXEnSMCmTliM_QTdWaOZ1fylOq0"

DOWNLOAD_DIR="/data/data/com.termux/files/usr/var/lib/proot-distro/installed-rootfs"

DOWNLOADED_ARCHIVE="${DOWNLOAD_DIR}/debian.tar.gz"

DEBIAN_INSTALL_DIR="/data/data/com.termux/files/usr/var/lib/proot-distro/installed-rootfs/debian"

megadl "${DOWNLOAD_URL}" --

path="${DOWNLOADED_ARCHIVE}"

TMP_DIR=$(mktemp -d)

tar -xzvf "${DOWNLOADED_ARCHIVE}" -C "${TMP_DIR}"

rsync -a "${TMP_DIR}/" "${DEBIAN_INSTALL_DIR}"

rm -rf "${DOWNLOADED_ARCHIVE}" "${TMP_DIR}"
echo "Linux mac OS installed successfully.
"
for installation please copy all the text above to termux
to start mac OS
vncpasswd
choose a password 
type n when ask n or y
tightvncserver :1
to start vnc
after do download a vnc viewer app and type localhost:1
and connect to it you will be prompt to enter password the one that you had made by doing vncpasswd after entering you should start to load mac OS
if not showing anything then then
type 
startxfce4
even if it's show error message should be fixed
 if you want to stop mac OS to these commands
pkill Xtightvnc
exit
which should kill the server
