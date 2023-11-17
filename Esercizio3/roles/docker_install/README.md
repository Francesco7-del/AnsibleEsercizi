# Ruolo Ansible per installazione Docker

Questo ruolo Ansible esegue l'installazione o la rimozione di Docker a seconda se sia già presente o meno.

## Requisiti

- Accesso root alla macchina target
- python e ansible installati sulla macchina di controllo

## Variabili

Questo ruolo utilizza le seguenti variabili:

- `docker_package`: nome del pacchetto Docker da installare (default: `docker-ce`)
- `docker_service`: nome del servizio systemd per Docker (default: `docker`)

## Come funziona

Il ruolo esegue i seguenti passi:

1. Raccoglie i facts sui pacchetti installati
2. Verifica se Docker è installato controllando la presenza del pacchetto
3. Se Docker è installato, arresta e disinstalla il servizio e il pacchetto
4. Se Docker non è installato, installa il pacchetto docker-ce
5. Avvia il servizio docker dopo l'installazione
6. Stampa lo stato corrente dell'installazione di Docker

In questo modo il ruolo gestisce in modo idempotente l'installazione o la rimozione di Docker a seconda dello stato corrente del sistema.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
