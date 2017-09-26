# Reporting role

Automates reporting scripts deployment.

## Manually running

### Payments reconciliation

The script is placed on the database server in the /bin directory and must be ran as the postgres user

To run against yesterday:

```bash
sudo -u postgres payment-reconciliation
```

To run against any date:

```bash
sudo -u postgres payment-reconciliation 2017-07-01
```

## License

MIT

## Testing

```bash
$ molecule test
```

