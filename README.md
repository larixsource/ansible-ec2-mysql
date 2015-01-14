ansible-ec2-mysql
=========

> [Ansible](http://www.ansible.com) role to install [MySQL](http://www.mysql.com) in Ubuntu Trusty, in EC2 using an EBS volume.

This role performs an standard installation in Trusty (`apt-get install mysql-server`), runs `mysql_secure_installation` and configures the server to use an EBS volume following the instructions of https://aws.amazon.com/articles/1663.

Requirements
------------

None.

Role Variables
--------------

- `mysql_version`: mysql server version, by default 5.5 (5.6 also available)
- `mysql_use_ebs`: if an EBS volume should be used, by default false
- `mysql_ebsdev`: EBS volume block device, by defaul xvdf
- `mysql_root_passwd`: mysql root password, by default 'supersecret', yo should overwrite this
- `mysql_rm_anon_user`: if the anonymous user should be removed (y or n), by default y
- `mysql_disallow_root_remote_login`: if the remote root login should be disallowed (y or n), by default y
- `mysql_rm_test_db`: if the test database should be removed (y or n), by default y

Dependencies
------------

None.

Example Playbook
----------------

The two relevant variables are `mysql_ebsdev` and `mysql_root_password`, the former is the block device associated to the EBS volume (in Trusty will be xvdf, xvdg, xvdh, and so on) and the later is the password of the root user (in mysql, obviously).

```yml
- hosts: servers
  roles:
     - { role: larixsource.ec2-mysql, mysql_ebsdev: 'xvdg', mysql_root_password: 'supersecret' }
```

Also, there's an example of provisioning with Vagrant in a local VM in the directory `test`.

License
-------

Apache-2.0

Author Information
------------------

Courtesy of [Larix](http://www.larix.cl) team.
