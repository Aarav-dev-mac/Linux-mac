# Linux-mac
Linux Mac OS for termux installation link provided in readme and also details

This project provides a script to set up a MacOS-like Debian environment on Termux. The script downloads a pre-configured Debian environment and synchronizes it with the existing installation without deleting any files.

## Features

- MacOS-like interface for Debian in Termux
- Easy setup script
- Ensures existing files are not deleted during synchronization

## Installation

#!/bin/bash
apt update && apt upgrade -y
pkg install -y megatools wget proot-distro rsync
proot-distro install debian
DOWNLOAD_URL="https://mega.nz/file/Fa0DjSAb#3bWB5YK9H7ztBK8wLXEnSMCmTliM_QTdWaOZ1fylOq0"
DOWNLOAD_DIR="/data/data/com.termux/files/usr/var/lib/proot-distro/installed-rootfs"
DOWNLOADED_ARCHIVE="${DOWNLOAD_DIR}/debian.tar.gz"
DEBIAN_INSTALL_DIR="/data/data/com.termux/files/usr/var/lib/proot-distro/installed-rootfs/debian"
megadl "${DOWNLOAD_URL}" --path="${DOWNLOADED_ARCHIVE}"
TMP_DIR=$(mktemp -d)
tar -xzvf "${DOWNLOADED_ARCHIVE}" -C "${TMP_DIR}"
rsync -a "${TMP_DIR}/" "${DEBIAN_INSTALL_DIR}"
rm -rf "${DOWNLOADED_ARCHIVE}" "${TMP_DIR}"
echo "Debian environment updated successfully."
for installation please copy all the text above to termux
