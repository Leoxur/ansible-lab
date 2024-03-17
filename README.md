# Laboratorio Docker con Ansible e due macchine di destinazione
- Questo codice crea tre immagini Docker, una come controller Ansible e due macchine di destinazione (con sistema operativo Rocky Linux 9).

- Clona questo repository oppure estrai il sorgente dal tar.

- Esegui il seguente comando:
`docker compose up -d --build`

- Connect to Ansible container:
```
docker exec -it ansible_lab /bin/bash
```
- Check target machine's connection and run playbook:
```
ssh server01@ansible
exit
ssh server02@ansible
exit
ansible -m ping -i inventory.ini target
```

Customizzato e forkato da https://github.com/fortinux/ansible-lab/tree/main
