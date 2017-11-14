Networker
=========
Install EMC's [Networker](https://www.emc.com/data-protection/networker.htm) in servers and clients.

This role install Network in servers and clients. Use `networker_mode` to select which installation to use. Currently, an independent storage node is not supported and is installed together with the server.

Packages are expected to be in an archive (`tar` or `zip`) as downloaded from EMC's site. The URL to this archive needs to be specify in `networker_package_url`, there is no default. Note that you might need to specify Networker's version in `networker_version` if different from the default (`8.2.4.9-1`).

This role currently does not initialize the console server. You need to manually run it and start the console service:
```
/opt/lgtonmc/bin/nmc_config
service gst start
```

Installation is based on the [official documentation](https://www.emc.com/collateral/TechnicalDocument/docu57695.pdf).

Requirements
------------
See `meta/main.yml`.

Role Variables
--------------
See `defaults/main.yml` for all options.

Dependencies
------------
None.

Example Playbook
----------------
Example:
```
- hosts: server
  roles:
    - {role: networker, mode: server}

- hosts: clients
  roles:
    - {role: networker, mode: client}
```

TODO
----
- Support upgrades
- Automatically configure console server and enable gst service
- Test on rhel 7
- Support storage nodes

Licence
-------
Released under the [MIT license](https://opensource.org/licenses/MIT).

Author Information
------------------
Luis Gracia while at [The Rockefeller University](https://www.rockefeller.edu):
- lgracia [at] rockefeller.edu
- GitHub at [luisico](https://github.com/luisico)
- Galaxy at [luisico](https://galaxy.ansible.com/luisico)
