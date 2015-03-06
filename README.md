Openshift Enterprise 3
======================

This vagrant environment will get you up to speed with https://github.com/openshift/training/blob/master/beta-1-setup.md.

Setup
-----

Grab the `rhel-7.0-64` vagrant box and install locally.

```bash
$ mkdir certificates secrets
$ cat > secrets/rhn.yml << EOF
rhn_username: XXXXXXXX
rhn_password: XXXXXXXX
EOF
$ vagrant up
```

At this point you can checkout the training repository and follow along on master.
