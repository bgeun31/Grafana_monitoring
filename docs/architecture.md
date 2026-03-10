# Architecture (Phase 1)

## Scope

Phase 1 focuses on a single VM deployment that is fully reproducible through Ansible.

## Components

- `Ansible`: host setup and deployment automation
- `Docker Engine + Compose`: runtime for containers
- `Prometheus`: metric collection
- `Grafana`: visualization and dashboarding

## Runtime Flow

1. Ansible installs Docker on the VM.
2. Ansible syncs `docker/` assets to `/opt/monitoring`.
3. Ansible executes `docker compose up -d`.
4. Prometheus scrapes itself and exposed targets.
5. Grafana automatically loads datasource/dashboard provisioning.

## Next Phases

- Phase 2: container image standardization + CI checks
- Phase 3: Kubernetes manifests/Helm + CD pipeline

