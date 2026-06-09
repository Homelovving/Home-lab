# Homelab

## What this is

A self-hosted learning environment I'm building to develop hands-on skills
in cloud infrastructure and networking — from the ground up, on my own hardware,
on my own time.

## Why

I come from a media and communications background. Not the most technical
discipline — but I've had an itch for this side of tech for a while, and this
summer I decided to do something about it.

I recently wrapped up Google Cloud Fundamentals: Core Infrastructure with
Coursera. The course gave me the concepts. This homelab is where I find out
if I actually understood them.

The plan is simple: build, break, fix, document. Publicly.

## What's coming

- Initial OS and network setup
- Self-hosted services (to be listed as the build progresses)
- Full documentation of every step — including the mistakes

## Follow along

- **Commits:** the history is all here
- **LinkedIn:** announcement post linked once published
- Updates on major milestones as they happen

---

## Progress

- **June 8, 2026:** Initial setup complete
  - Created Ubuntu Server 24.04 LTS (ARM64) VM on UTM
  - Allocated 8GB RAM, 4 CPU cores, 60GB storage
  - Configured LVM storage layout
  - Installed OpenSSH Server
  - Successfully SSH'd into the server from macOS Terminal

---
- **June 9, 2026:** Docker installation and configuration
  - installed security certificates and download tool needed for Docker setup using:
    ```
    sudo apt install ca-certificates curl
    ```
  - created a directory to store Docker's cryptographic verification key using:
    ```
    sudo install -m 0755 -d /etc/apt/keyrings
    ```
  - downloaded and stored Docker's official GPG key for package verification using:
    ```
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    ```
  - registered Docker's official   repository as a trusted software source using:
    ```
    echo "deb [arch=arm64 signed-by=...] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```
  - refreshed package lists to include Docker's repository using:
    ```
    sudo apt update
    ```
  - installed Docker engine, CLI, runtime, and plugins using:
    ```
    sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    ```
  - added user to docker group to run Docker commands without sudo using:
    ```
    sudo usermod -aG docker $USER
    ```
  - verified Docker installation was working correctly using:
    ```
    docker run hello-world
    ```
  - confirmed Docker Compose v5.1.4 installed using:
    ```
    docker compose version
    ```
  - All commands sourced from official Docker documentation: docs.docker.com/engine/install/ubuntu

- **June 9, 2026:** Jellyfin media server deployment
  - created dedicated directory for Jellyfin using:
    ```
    mkdir -p ~/homelab/jellyfin
    ```
  - navigated into Jellyfin directory
    ```
    cd ~/homelab/jellyfin
    ```
  - created Docker Compose configuration file defining Jellyfin's image, ports, and persistent volumes
    ```
    nano docker-compose.yml
    ```
  - pulled Jellyfin image from Docker Hub and started container in background using:
    ```
    docker compose up -d
    ```
  - verified Jellyfin container was running and healthy on port 8096 using:
    ```
    docker ps
    ```
  - Completed Jellyfin initial setup via browser at http://[server-ip]:8096

- **June 9, 2026:** Issues encountered and fixes
  - Media folder permissions denied — Docker created the media folder as root, blocking file uploads via scp. Fixed with
    ```
    sudo chown -R $USER:$USER ~/homelab/jellyfin/media
    ```
    which transferred folder ownership to current user
  - Interface confusion — initially attempted to play videos from the Dashboard (admin/settings area) instead of the Home screen. Videos are played from the Jellyfin home screen, accessible by clicking the Jellyfin logo. Dashboard is for server administration only. Both MOV and MP4 files confirmed playing correctly from home screen.
  - Diagnosed container issues using
    ```
    docker logs jellyfin
    ```


*This repo is a work in progress. Check back soon.*
