# Ruolo Ansible per installazione Docker

Questo ruolo Ansible esegue l'installazione o la rimozione di Docker a seconda se sia già presente o meno.

## Requisiti

- Accesso root alla macchina target
- python e ansible installati sulla macchina di controllo

## Variabili

Questo ruolo utilizza le seguenti variabili:

- `docker_package`: nome del pacchetto Docker da installare (default: `docker-ce`)
- `docker_service`: nome del servizio systemd per Docker (default: `docker`)
-  `docker_packages`: pacchetti utilizzati per l'installazione e disinstallazione

## Come funziona

Il ruolo esegue i seguenti passi:

1)Se Docker era installato e viene rimosso, il task successivo stampa un messaggio usando debug.

2)Viene quindi installato Docker tramite il modulo package, specificando i pacchetti necessari in docker_packages.

3)Dopo l'installazione, il modulo package_facts raccoglie informazioni sui pacchetti installati e i risultati vengono registrati in pkg_facts.

4)Il task successivo stampa a video la lista dei pacchetti Docker installati, filtrando il risultato di pkg_facts.

5)Infine il servizio Docker viene avviato e abilitato all'avvio tramite il modulo service.

Il ruolo gestisce quindi il ciclo di vita completo di installazione e configurazione iniziale di Docker.


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
       - role: docker_install

    - name: includi role per installazione di docker
      include_role: 
        name: docker_install

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
