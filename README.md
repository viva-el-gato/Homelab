# Homelab Infrastructure

## Overview

This repository contains the source-controlled configuration for my homelab infrastructure. Its purpose is to provide a single source of truth for Docker Compose stacks, application configuration, deployment scripts, and infrastructure documentation.

The environment is designed around AI services, automation, self-hosted applications, and infrastructure management running on Proxmox and Docker.

---

## Objectives

* Version control all Docker Compose files
* Maintain reproducible infrastructure
* Simplify disaster recovery
* Track configuration changes over time
* Enable easy deployment through Portainer
* Keep secrets separate from source control

---

## Repository Structure

```text
homelab/
├── ai-stack/
│   ├── llama.cpp/
│   ├── litellm/
│   ├── open-webui/
│   ├── qdrant/
│   └── searxng/
│
├── agents/
│   ├── hermes/
│   └── openclaw/
│
├── infrastructure/
│   ├── portainer/
│   ├── syncthing/
│   ├── watchtower/
│   └── monitoring/
│
├── homeassistant/
│
├── proxmox/
│
├── scripts/
│
├── docs/
│
├── .gitignore
└── README.md
```

---

## Deployment

Stacks are deployed and managed using **Portainer**.

Each application directory contains its own Docker Compose configuration and any supporting configuration files required for deployment.

Example:

```text
agents/
└── hermes/
    ├── compose.yaml
    ├── .env.example
    └── README.md
```

---

## Git Workflow

Typical workflow:

1. Modify configuration.
2. Test locally.
3. Commit changes.
4. Push to GitHub.
5. Redeploy the updated stack using Portainer.

Example:

```bash
git add .
git commit -m "Update Hermes configuration"
git push
```

---

## Security

The following files should **never** be committed:

* `.env`
* API keys
* Passwords
* Tokens
* SSH keys
* TLS certificates
* Database files
* Docker volumes
* AI model files (`*.gguf`, `*.safetensors`)

Use `.env.example` files to document required environment variables.

---

## Technologies

### Virtualization

* Proxmox VE

### Container Management

* Docker
* Portainer

### AI Stack

* llama.cpp
* LiteLLM
* Open WebUI
* Qdrant
* SearXNG

### Agents

* Hermes
* OpenClaw

### Infrastructure

* Syncthing
* Watchtower

### Automation

* Home Assistant

---

## Backup Strategy

Configuration is backed up through Git.

Persistent application data is stored separately and backed up independently.

Restoring the environment consists of:

1. Install Docker.
2. Install Portainer.
3. Clone this repository.
4. Deploy the required stacks.
5. Restore application data and secrets.

---

## License

This repository contains personal homelab infrastructure and is intended for private use.
