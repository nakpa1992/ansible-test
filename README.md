# Ansible Praktický test — INIZIO Internet Media s.r.o.

## Cíl
Pomocí Ansible automatizovat instalaci a zabezpečení webového serveru na Ubuntu 22.04. 
Playbook nainstaluje a nakonfiguruje NGINX, nasadí jednoduchý web a nastaví základní bezpečnostní prvky systému.

---

##Co playbook dělá
- Instaluje NGINX, UFW, Fail2ban a Unattended-Upgrades
- Vytváří uživatele `webapp` a nasazuje webové soubory do `/opt/static-sites`
- Nahrazuje výchozí konfiguraci NGINX vlastní šablonou
- Aktivuje firewall (UFW) – povoluje pouze porty 22 a 80
- Zabezpečuje SSH:
  - Zakazuje přihlášení uživatele root 
  - Povoluje pouze přihlášení pomocí SSH klíče
- Aktivuje automatické bezpečnostní aktualizace
- Ověřuje funkčnost webu pomocí modulu `uri`

---

## Spuštění
*1 Přejdi do složky projektu:*

```bash
cd ~/ansible-test```

*2 Spusť playbook*

```bash
ansible-playbook -i inventory/hosts.ini playbooks/main.yml --ask-become-pass```

*3 Ověření funkčnosti*

```bash
curl http://localhost
sudo ufw status
systemctl is-active nginx
systemctl is-active fail2ban```

## Očekávaný výstup

Když se po zadání ```curl http://localhost``` zobrazí:

<h1>Vitej u nakpi!</h1>

znamená to, že webový server i konfigurace Ansible fungují správně.


## Poznámky

- Playbook je idempotentní - opakované spuštění neprovádí zbytečné změny.
- SSH přístup je možný pouze pomocí klíče.
- Projekt byl testován v prostředí **Ubuntu 22.04**

## Autor

**Tomáš Panský**

[github] (https://github.com/nakpa1992)

