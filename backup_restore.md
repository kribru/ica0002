Install and configure infrastructure with Ansible:

Use this command under the project directory:

    ansible-playbook infra.yaml

Restore MySQL data from the backup:
Use these commands on the managed host:

    sudo -u backup duplicity --no-encryption restore rsync://kribru@backup.kify.ki//home/kribru/ /home/backup/restore/
    sudo -u root mysql agama < /home/backup/restore/agama.sql

add a few words here how the result of backup restore can be checked

To Restore Influxdb data from the backup:
Use these commands on the managed host:

    service telegraf stop
    influx -execute 'DROP DATABASE telegraf'
    influxd restore -portable -database telegraf /home/backup/influxdb

To start the Telegraf service run: 

Use this command under the project directory:

    ansible-playbook infra.yaml
