apache
==========

Installs, secures Apache2, and configures sites.

Requirements
------------

None.

Role Variables
--------------

`_apache` is used to configure apache and sites.

Dependencies
------------

None.

Example Playbook
----------------

```
    - hosts: servers
      vars:
        APACHE:
          use_default_config: False
          listen:
            - { ip: localhost, port: 80 }
          modules:
            disable: []
            enable: []
          sites:
            - name: heimbot
              enabled: True
              vhost: localhost
              port: 80
              document_root: /var/www
              server_admin: info@heimbot
              extra: |+
                <Directory "/var/www">
                    AllowOverride All
                    Require all granted
                </Directory>
      roles:
        - { role: apache, tags: [ 'apache' ], _apache: "{{ APACHE }}" }
```

License
-------

See LICENSE file.

Author Information
------------------

Initially created by Lukas Pustina [@drivebytesting](https://twitter.com/drivebytesting).

