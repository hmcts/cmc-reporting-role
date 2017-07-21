Payment reconciliation role
=========

Automates adding a script for payment reconciliation

Manually running
-------
The script is placed on the database server in the /bin directory and must be ran as the postgres user

To run against yesterday:
```
sudo -u postgres payment-reconciliation
```

To run against any date:
```
sudo -u postgres payment-reconciliation 2017-07-01
```


License
-------

MIT

Testing
------------------

```
$ molecule test
```

