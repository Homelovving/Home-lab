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
  - Installed Docker CE, Docker CLI, containerd, 
    Buildx and Compose plugins
  - Added user to docker group — sudo no longer 
    required for docker commands
  - Verified Docker engine working via hello-world container
  - Docker Compose v5.1.4 confirmed installed
  - All installation commands sourced from official 
    Docker documentation (docs.docker.com)
    
*This repo is a work in progress. Check back soon.*
