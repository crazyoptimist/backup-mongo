# Backup MongoDB

_AWS RDS-like backup service for mongo_

This application creates complete backups of a MongoDB database.

It behaves like the backup system in AWS RDS, i.e., it removes old backups, then creates a new backup. You can configure the retention period in weeks like in AWS RDS.

It's possible to configure the cron expression according to your needs, refer [cron expression generator](https://crontab.cronhub.io/).

It supports two storage types as of now, `local` and `aws`.

## Deployment

### Configuration

Nothing complex, just create your own `.env` file.

```bash
cp .env.example .env
```

### Deploy Using Docker(Compose)

```bash
docker-compose up -d
```

### Deploy Using PM2

Have mongodb(version >= 3.6) installed on your operating system first.

```bash
mkdir backups
npm install --global pm2@latest
pm2 start index.js
```

## Restoration From Backup Files

```bash
node restore --file=filename.gz --fromDB=aaa --toDB=bbb
```

In the command, `filename.gz` is a backup file generated by this application inside the `local_backups` directory.

`aaa` is the original db name, `bbb` is the destination db name, which are optional.

## License

MIT

Coded with :heart: by [crazyoptimist](https://github.com/crazyoptimist)
