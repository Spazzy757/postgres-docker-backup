# postgres-docker-backup
This is a container that can be run to create backups of a postgres db on the containers networks

## ENVIRONMENT
> The scripts runs off environment variables

```bash
# Optional system user to run backups as.  If the user the script is running as doesn't match this
# the script terminates.  Leave blank to skip check.
BACKUP_USER

# Optional hostname to adhere to pg_hba policies.  Will default to "localhost" if none specified.
HOSTNAME

# Optional username to connect to database as.  Will default to "postgres" if none specified.
USERNAME

# This dir will be created if it doesn't exist.  This must be writable by the user the script is
# running as.
BACKUP_DIR

# List of strings to match against in database name, separated by space or comma, for which we only
# wish to keep a backup of the schema, not the data. Any database names which contain any of these
# values will be considered candidates. (e.g. "system_log" will match "dev_system_log_2010-01")
SCHEMA_ONLY_LIST

# Will produce a custom-format backup if set to "yes"
ENABLE_CUSTOM_BACKUPS

# Will produce a gzipped plain-format backup if set to "yes"
ENABLE_PLAIN_BACKUPS

# Will produce gzipped sql file containing the cluster globals, like users and passwords, if set to "yes"
ENABLE_GLOBALS_BACKUPS
```

## RESOURCES

https://wiki.postgresql.org/wiki/Automated_Backup_on_Linux