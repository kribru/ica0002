Install and configure infrastructure with Ansible:

Use this command under the project directory:

    ansible-playbook infra.yaml

To restore MySQL data from the backup: 

Use these commands on the managed host with Mysql:

    sudo -u backup duplicity --no-encryption restore rsync://kribru@backup.kify.ki//home/kribru/ /home/backup/restore/
    sudo -u root mysql agama < /home/backup/restore/agama.sql

First line should say when the backup was done, second shouldn't show anything.

Now if you check the Agama webpage, the data should be restored.

---
To Restore Influxdb data from the backup:

Use these commands on the managed host with InfluxDB:

    service telegraf stop
    influx -execute 'DROP DATABASE telegraf'
    influxd restore -portable -database telegraf /home/backup/influxdb

To start the Telegraf service: 

Run this command under the project directory:

    ansible-playbook infra.yaml
