
# Ruolo Ansible per l'installazione di Apache
Questo ruolo Ansible gestisce l'installazione e la configurazione di Apache su una macchina target. Supporta sia le distribuzioni basate su Debian che quelle basate su RedHat (Fedora/Centos).

## Requisiti
- Disporre dell'escalation ai privilegi di root per accedere alle macchine target.
- Abilitare la raccolta dei facts in Ansible (gather_facts: true).

## Variabili
Il ruolo utilizza le seguenti variabili:

`pkg_name`: Il nome del pacchetto Apache da installare (impostato di default su httpd per Fedora/Centos/RedHat e apache2 per Debian).

`blacklist_url`: L'URL da cui scaricare la blacklist.

`service_apache`: Il nome del servizio systemd per Apache (impostato di default su pkg_name).

`configuration_path`: Il percorso della configurazione di Apache.

`configuration_file_path`: Il percorso del file di configurazione di Apache.

`html_directory`: La directory in cui creare la pagina web personalizzata.

`html_file`: Il percorso del file HTML da creare.

`html_content`: Il contenuto HTML da inserire nella pagina web personalizzata.

## Funzionalità ruolo
  Questo ruolo Ansible esegue le seguenti operazioni:
  1. Installa il pacchetto Apache (`httpd` o `apache2` a seconda della distribuzione del sistema operativo).
  2. Scarica una blacklist da un URL specificato.
  3. Esegue il parsing della blacklist e la aggiunge alla configurazione di Apache.
  4. Crea una pagina web personalizzata.

## Test eseguti
- Test fatti con OS Ubuntu e Fedora
- Installazione pulita dove Apache non presente,test con Apache presente sulla macchina target--> esito positivo
- Test effettuato IP, con presenza non fa visualizza la Pagina di 'Benvenuto', con assenza di IP nella blacklist visualizza la Pagina di 'Benvenuto--> esito positivo
- Test con blacklist in stato: aggiornato,non aggiornato -->esito positivo
- Test aggiornamento,creazione pagina di 'Benvenuto'--> esito positivo

## Esempio di Playbook
Ecco un esempio di come utilizzare il ruolo:

```yaml
- hosts: servers
  roles:
   - role: apache_install
```

```yaml
- name: includi ruolo per installazione di Apache
  include_role:
    name: apache_install
```
