# Linux-mac
Linux Mac OS for termux installation link provided in readme and also details

This project provides a script to set up a MacOS-like Debian environment on Termux. The script downloads a pre-configured Debian environment and synchronizes it with the existing installation without deleting any files.

## Features

- MacOS-like interface for Debian in Termux
- Easy setup script
- Ensures existing files are not deleted during synchronization

## Installation

#!/bin/bash

# Update and upgrade packages
apt update && apt upgrade -y

# Install necessary packages
pkg install -y megatools wget proot-distro rsync

# Install Debian using proot-distro
proot-distro install debian

# Define the URL of the tar archive to download
DOWNLOAD_URL="https://mega.nz/file/Fa0DjSAb#3bWB5YK9H7ztBK8wLXEnSMCmTliM_QTdWaOZ1fylOq0"

# Define the path where the tar archive will be downloaded
DOWNLOAD_DIR="/data/data/com.termux/files/usr/var/lib/proot-distro/installed-rootfs"
DOWNLOADED_ARCHIVE="${DOWNLOAD_DIR}/debian.tar.gz"

# Define the path where Debian is installed
DEBIAN_INSTALL_DIR="/data/data/com.termux/files/usr/var/lib/proot-distro/installed-rootfs/debian"

# Download the tar archive using megatools
megadl "${DOWNLOAD_URL}" --path="${DOWNLOADED_ARCHIVE}"

# Extract the downloaded tar archive to a temporary directory
TMP_DIR=$(mktemp -d)
tar -xzvf "${DOWNLOADED_ARCHIVE}" -C "${TMP_DIR}"

# Copy files from the temporary directory to the Debian installation directory
# Overwrite existing files, but do not delete any files in the original directory
rsync -a "${TMP_DIR}/" "${DEBIAN_INSTALL_DIR}"

# Cleanup: Remove the downloaded tar archive and temporary directory
rm -rf "${DOWNLOADED_ARCHIVE}" "${TMP_DIR}"

echo "Debian environment updated successfully."
for installation please copy all the text above to termux
