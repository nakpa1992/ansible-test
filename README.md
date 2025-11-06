# Ansible Project

Tento projekt slouží k nastavení lokálního webového serveru s NGINX pomocí Ansible.

## Struktura projektu

- `inventory/` – seznam hostů
- `group_vars/` – proměnné pro skupiny hostů
- `playbooks/` – hlavní playbooky
- `roles/` – role, šablony, úlohy
- `README.md` – dokumentace projektu

## Spuštění

1. Spusť Ansible playbook:

```bash
ansible-playbook -i inventory/hosts.ini playbooks/main.yml

