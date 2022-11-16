# SVN Repository Backup

Backs up a directory full of subversion repositories to S3. Configuration for automatic backups is outlined below.

## Configuration

Create a file in /etc/repository-backup.conf with the following contents:

```
AWS_ACCESS_KEY=<your key>
AWS_SECRET_ACCESS_KEY=<your other key>
AWS_REGION=<your region>
AWS_BUCKET=<bucket path, without s3://>
```

## Timer

```
[Unit]
Description=Daily Repository Backup

[Timer]
OnCalendar=*-*-* 01:30:00

[Install]
WantedBy=timer.target
```

## Service

```
[Unit]
Description=Repository Backup

[Service]
Type=oneshot
ExecStart=/usr/local/bin/repository-backup
```
