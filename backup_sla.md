We are backing up:

    Database servers(MySql)
    InfluxDB
    Ansible repository

Backup coverage
    
    From Mysql we are backing up sqldump.
    From InfluxDB we are backing up the data.
    And also backing up the whole ansible repository.

RPO (recovery point objective)

    We will backup our services twice a day, so every 12 hours(10:22 and 22:22 UTC).

Versioning and retention

    We are keeping 1 backup version and we will store it for a week.

Usability checks

     We have a seperate environment where we take one backup 
     and check if it is functional or not.

Restoration criteria

     It should be restored when something is not working.

RTO (recovery time objective)

    Restoring the system will take max 2 hours.
