# Ruolo Ansible per l'installazione di Docker

Questo ruolo Ansible gestisce l'installazione e l'aggiornamento di Docker su una macchina target. Supporta sia le distribuzioni basate su Debian che quelle basate su RedHat(Fedora/Centos).

## Requisiti
- Disporre dell'escalation ai privilegi di root per accedere alle macchine target 
- Abilitare raccolta facts in Ansible (gather_facts: true)
- Docker non è supportato dalle versioni precedenti a Centos7 e Ubuntu <20


## Variabili
Il ruolo utilizza le seguenti variabili:

`docker_service`: Il nome del servizio systemd per Docker (impostato di default su docker).

`repo_baseurl_rh_family`, `repo_name_rh_family`, `repo_file_rh_family`, `repo_desc_rh_family`, `repo_gpk_rh_family`: Queste variabili definiscono il repository Docker ufficiale per le distribuzioni basate su RedHat.

`docker_packages_remove_rh`: Una lista di vecchi pacchetti Docker da rimuovere.

`docker_packages_install`: Una lista di pacchetti Docker da installare su distribuzioni basate su RedHat.
(La versione per un'installazione specifica può essere fatta come mostrato nell'esempio nel file inventory.ini.)

`docker_allow_downgrade`: Un flag booleano che, se impostato su true, consente il downgrade dei pacchetti durante l'installazione.

`repo_baseurl_debian_family`: Questa variabile definisce il repository Docker ufficiale per le distribuzioni basate su Debian.

`docker_packages_inst_ubuntu`: Una lista di pacchetti Docker da installare su distribuzioni basate su Debian. Se viene specificata una versione per un pacchetto (ad esempio, docker-ce=5:24.0.6-1~ubuntu.22.04~jammy), verrà installata quella versione. In caso contrario, verrà installata l'ultima versione disponibile.
.

## Esempio di Playbook

Ecco 2 esempi di come utilizzare il  ruolo:

```yaml
- hosts: servers
  roles:
   - role: docker_install
```

```yaml
- name: includi role per installazione di docker
  include_role: 
    name: docker_install
```
