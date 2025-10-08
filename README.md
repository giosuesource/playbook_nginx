## Playbook Ansible per Nginx

Questo repository contiene un playbook Ansible per la configurazione di Nginx su VM target. Il playbook si occupa del deploy di un file di configurazione generato tramite template Jinja2, adattato ai singoli host.

## Struttura del repository

- `playbook.yml`: playbook principale. Utilizza il modulo `template` per generare la configurazione Nginx partendo da un file `.j2`.
- `templates/nginx.conf.j2`: template Jinja2 della configurazione Nginx. I valori dinamici vengono forniti dai file in `host_vars`.
- `host_vars/<hostname>.yml`: variabili specifiche per ciascun host. 
- `inventory.ini`: file contenente indirizzi ip, nomi delle macchine e utenti abilitati alla connessione ssh, i quali  permetteranno l' esecuzione del playbook.

##  Requisiti

- Ansible >= 2.9
- Accesso SSH ai nodi target
- Presenza di Nginx installato nella path `/usr/local/nginx-1.26.2/`
- Il servizio Nginx deve essere gestito come `nginx-custom` (modificabile tramite handler)

## Esecuzione

Eseguire il playbook con:

```bash
ansible-playbook -i inventory playbook.yml

