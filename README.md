# Grafana Monitoring Platform (MVP)

This repository contains a practical starting point for:

- provisioning Linux VM hosts with Ansible
- deploying Grafana + Prometheus with Docker Compose
- managing Grafana datasources/dashboards as code

## Project Structure

```text
.
├─ ansible/
│  ├─ ansible.cfg
│  ├─ inventories/
│  │  └─ dev/hosts.ini
│  ├─ group_vars/all.yml
│  ├─ playbooks/site.yml
│  └─ roles/
│     ├─ common/
│     ├─ docker/
│     └─ grafana_stack/
├─ docker/
│  ├─ docker-compose.yml
│  ├─ grafana/
│  │  ├─ dashboards/system-overview.json
│  │  └─ provisioning/
│  │     ├─ dashboards/dashboard.yml
│  │     └─ datasources/prometheus.yml
│  └─ prometheus/prometheus.yml
└─ docs/
   └─ architecture.md
```

## Prerequisites

- control machine with Ansible installed
- target Linux VM (Ubuntu/Debian recommended)
- SSH key-based access to target VM
- target user with sudo privilege

## Quick Start

1. Edit inventory:

```ini
# ansible/inventories/dev/hosts.ini
[monitoring]
your-vm-ip ansible_user=ubuntu ansible_become=true
```

2. (Optional) update defaults:

```yaml
# ansible/group_vars/all.yml
grafana_admin_password: "change-me"
```

3. Run playbook:

```bash
cd ansible
ansible-playbook -i inventories/dev/hosts.ini playbooks/site.yml
```

4. Access services:

- Grafana: `http://<vm-ip>:3000`
- Prometheus: `http://<vm-ip>:9090`

## Notes

- For production, use `ansible-vault` for secrets.
- Replace default admin password and restrict inbound ports.
- This is a baseline for adding Kubernetes and CI/CD in the next phase.

