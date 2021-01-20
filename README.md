FRR
=========

An ansible role to manage [Free Range Routing](https://frrouting.org/)

Requirements
------------

N/A

Role Variables
--------------

| Variable                    | Purpose                                                         | Type    | Default                                | Note                                                                          |
| --------------------------- | --------------------------------------------------------------- | ------- | -------------------------------------- | ----------------------------------------------------------------------------- |
| `frr_manage_repo`           | Determines if this role will add the FRR repository             | bool    | true                                   |                                                                               |
| `frr_update_pkg_cache`      | Update package cache prior to installing FRR                    | bool    | true                                   |                                                                               |
| `frr_daemon_file`           | Full path to FRR daemons file                                   | string  | '/etc/frr/daemons'                     |                                                                               |
| `frr_config_file`           | Full path to FRR config                                         | string  | '/etc/frr/frr.conf'                    |                                                                               |
| `frr_babeld_enabled`        | Enables the Babel daemon                                        | bool    | false                                  | Automatically set to true when `frr_config_babel_raw` is defined              |
| `frr_bfdd_enabled`          | Enables the Bidirectional Forwarding Detection daemon           | bool    | false                                  | Automatically set to true when `frr_config_bfd_raw` is defined                |
| `frr_bgpd_enabled`          | Enables the Border Gateway Protocol daemon                      | bool    | false                                  | Automatically set to true when `frr_config_bgp_raw` is defined                |
| `frr_eigrpd_enabled`        | Enables the Enhanced Interior Gateway Routing Protocol daemon   | bool    | false                                  | Automatically set to true when `frr_config_eigrp_raw` is defined              |
| `frr_fabricd_enabled`       | Enables the OpenFabric daemon                                   | bool    | false                                  | Automatically set to true when `frr_config_fabric_raw` is defined             |
| `frr_isisd_enabled`         | Enables the Intermediate System to Intermediate System daemon   | bool    | false                                  | Automatically set to true when `frr_config_isis_raw` is defined               |
| `frr_ldpd_enabled`          | Enables the MPLS daemon                                         | bool    | false                                  | Automatically set to true when `frr_config_ldp_raw` is defined                |
| `frr_nhrpd_enabled`         | Enables the Next Hop Routing Protocol daemon                    | bool    | false                                  | Automatically set to true when `frr_config_nhrpd_raw` is defined              |
| `frr_ospf6d_enabled`        | Enables the Open Shortest Path First v3 daemon                  | bool    | false                                  | Automatically set to true when `frr_config_ospf6_raw` is defined              |
| `frr_ospfd_enabled`         | Enables the Open Shortest Path First v2 daemon                  | bool    | false                                  | Automatically set to true when `frr_config_ospf_raw` is defined               |
| `frr_pbrd_enabled`          | Enables the Protocol Independent Multicast daemon               | bool    | false                                  | Automatically set to true when `frr_config_pim_raw` is defined                |
| `frr_pimd_enabled`          | Enables the Policy Based Routing daemon                         | bool    | false                                  | Automatically set to true when `frr_config_pbr_raw` is defined                |
| `frr_ripd_enabled`          | Enables the Routing Information Protocol daemon                 | bool    | false                                  | Automatically set to true when `frr_config_rip_raw` is defined                |
| `frr_ripngd_enabled`        | Enables the Routing Information Protocol Next Generation daemon | bool    | false                                  | Automatically set to true when `frr_config_ripng_raw` is defined              |
| `frr_sharpd_enabled`        | Enables the Super Happy Advanced Routing Process daemon         | bool    | false                                  | Automatically set to true when `frr_config_sharp_raw` is defined              |
| `frr_staticd_enabled`       | Enables the Static Route daemon                                 | bool    | false                                  | Automatically set to true when `frr_config_sharp_raw` is defined              |
| `frr_vtysh_enable`          | Enables FRR vtysh                                               | bool    | true                                   |                                                                               |
| `frr_babeld_options`        | Babel daemon options                                            | string  | '"  --daemon -A 127.0.0.1"'            |                                                                               |
| `frr_bfdd_options`          | BFD daemon options                                              | string  | '"  --daemon -A 127.0.0.1"'            |                                                                               |
| `frr_bgpd_options`          | BGP daemon options                                              | string  | '"   --daemon -A 127.0.0.1"'           |                                                                               |
| `frr_eigrpd_options`        | EIGRP daemon options                                            | string  | '"  --daemon -A 127.0.0.1"'            |                                                                               |
| `frr_fabricd_options`       | Fabric daemon options                                           | string  | '"  --daemon -A 127.0.0.1"'            |                                                                               |
| `frr_isisd_options`         | ISIS daemon options                                             | string  | '"  --daemon -A 127.0.0.1"'            |                                                                               |
| `frr_ldpd_options`          | MPLS daemon options                                             | string  | '"  --daemon -A 127.0.0.1"'            |                                                                               |
| `frr_nhrpd_options`         | NHRP daemon options                                             | string  | '"  --daemon -A 127.0.0.1"'            |                                                                               |
| `frr_ospf6d_options`        | OSPFv3 daemon options                                           | string  | '" --daemon -A ::1"'                   |                                                                               |
| `frr_ospfd_options`         | OSPFv2 daemon options                                           | string  | '"  --daemon -A 127.0.0.1"'            |                                                                               |
| `frr_pbrd_options`          | PBR daemon options                                              | string  | '"  --daemon -A 127.0.0.1"'            |                                                                               |
| `frr_pimd_options`          | PIM daemon options                                              | string  | '"  --daemon -A 127.0.0.1"'            |                                                                               |
| `frr_ripd_options`          | RIP daemon options                                              | string  | '"   --daemon -A 127.0.0.1"'           |                                                                               |
| `frr_ripngd_options`        | RIPNG daemon options                                            | string  | '" --daemon -A ::1"'                   |                                                                               |
| `frr_sharpd_options`        | SHARP daemon options                                            | string  | '"  --daemon -A 127.0.0.1"'            |                                                                               |
| `frr_staticd_options`       | STATIC daemon options                                           | string  | '"  --daemon -A 127.0.0.1"'            |                                                                               |
| `frr_zebra_options`         | Zebra daemon options                                            | string  | '" -s 90000000 --daemon -A 127.0.0.1"' |                                                                               |
| `frr_max_fds`               | Max FDS                                                         | integer | `undefined`                            |                                                                               |
| `frr_watch_frr_options`     | WATCHFRR options                                                | string  | `undefined`                            |                                                                               |
| `frr_config_basic_raw`      | Basic Configuration                                             | string  | `undefined`                            | [Basic Documentation](http://docs.frrouting.org/en/latest/setup.html)         |
| `frr_config_filter_raw`     | Filter Configuration                                            | string  | `undefined`                            | [Filter Documentation](http://docs.frrouting.org/en/latest/filter.html)       |
| `frr_config_routemap_raw`   | Route Map Configuration                                         | string  | `undefined`                            | [Route Map Documentation](http://docs.frrouting.org/en/latest/routemap.html)  |
| `frr_config_interfaces_raw` | Interface Configuration                                         | string  | `undefined`                            | [Interface Documentation](http://docs.frrouting.org/en/latest/zebra.html#id3) |
| `frr_config_bfd_raw`        | BFD Configuration                                               | string  | `undefined`                            | [BFD Documentation](http://docs.frrouting.org/en/latest/bfd.html)             |
| `frr_config_bgp_raw`        | BGP Configuration                                               | string  | `undefined`                            | [BGP Documentation](http://docs.frrouting.org/en/latest/bgp.html)             |
| `frr_config_babel_raw`      | Babel Configuration                                             | string  | `undefined`                            | [Babel Documentation](http://docs.frrouting.org/en/latest/babeld.html)        |
| `frr_config_fabric_raw`     | OpenFabric Configuration                                        | string  | `undefined`                            | [OpenFabric Documentation](http://docs.frrouting.org/en/latest/fabricd.html)  |
| `frr_config_ldp_raw`        | MPLS Configuration                                              | string  | `undefined`                            | [MPLS Documentation](http://docs.frrouting.org/en/latest/ldpd.html)           |
| `frr_config_eigrp_raw`      | EIGRP Configuration                                             | string  | `undefined`                            | [EIGRP Documentation](http://docs.frrouting.org/en/latest/eigrpd.html)        |
| `frr_config_isis_raw`       | ISIS Configuration                                              | string  | `undefined`                            | [ISIS Documentation](http://docs.frrouting.org/en/latest/isisd.html)          |
| `frr_config_nhrpd_raw`      | NHRP Configuration                                              | string  | `undefined`                            | [NHRP Documentation](http://docs.frrouting.org/en/latest/nhrpd.html)          |
| `frr_config_ospf_raw`       | OSPFv2 Configuration                                            | string  | `undefined`                            | [OSPFv2 Documentation](http://docs.frrouting.org/en/latest/ospfd.html)        |
| `frr_config_ospf6_raw`      | OSPFv3 Configuration                                            | string  | `undefined`                            | [OSPFv3 Documentation](http://docs.frrouting.org/en/latest/ospf6d.html)       |
| `frr_config_pim_raw`        | PIM Configuration                                               | string  | `undefined`                            | [PIM Documentation](http://docs.frrouting.org/en/latest/pim.html)             |
| `frr_config_pbr_raw`        | PBR Configuration                                               | string  | `undefined`                            | [PBR Documentation](http://docs.frrouting.org/en/latest/pbr.html)             |
| `frr_config_rip_raw`        | RIP Configuration                                               | string  | `undefined`                            | [RIP Documentation](http://docs.frrouting.org/en/latest/ripd.html)            |
| `frr_config_ripng_raw`      | RIPNG Configuration                                             | string  | `undefined`                            | [RIPNG Documentation](http://docs.frrouting.org/en/latest/ripngd.html)        |
| `frr_config_sharp_raw`      | SHARP Configuration                                             | string  | `undefined`                            | [SHARP Documentation](http://docs.frrouting.org/en/latest/sharp.html)         |
| `frr_config_static_raw`     | Static Route Configuration                                      | string  | `undefined`                            | [Static Route Documentation](http://docs.frrouting.org/en/latest/static.html) |
| `frr_config_vrrp_raw`       | VRRP Configuration                                              | string  | `undefined`                            | [VRRP Documentation](http://docs.frrouting.org/en/latest/vrrp.html)           |
| `frr_config_bmp_raw`        | BGP Monitoring Configuration                                    | string  | `undefined`                            | [BMP Documentation](http://docs.frrouting.org/en/latest/bmp.html)                                                                              |

**Ubuntu Specific Variables**

| Variable            | Purpose                               | Type              | Default                                                                                      | Notes |
| ------------------- | ------------------------------------- | ----------------- | -------------------------------------------------------------------------------------------- | ----- |
| frr_packages        | FRR Packages to manage                | list (of strings) |                                                                                              |       |
| frr_package_state   | State of FRR Packages                 | string            | 'latest'                                                                                     |       |
| frr_service         | Name of FRR Service                   | string            | 'frr'                                                                                        |       |
| frr_service_state   | State of FRR Service                  | string            | 'started'                                                                                    |       |
| frr_service_enabled |                                       | string            | true                                                                                         |       |
| frr_apt_repo_state  | State of FRR Repository               | string            | 'present'                                                                                    |       |
| frr_apt_repo_file   | File to add Repository information to | string            | '/etc/apt/sources.list.d/frr.list'                                                           |       |
| frr_apt_gpg_key     | FRR GPG key                           | string            | 'https://deb.frrouting.org/frr/keys.asc'                                                     |       |
| frr_apt_release     | FRR Release                           | string            | 'frr-stable'                                                                                 |       |
| frr_apt_repo        | FRR Repository                        | string            | "deb https://deb.frrouting.org/frr {{ ansible_distribution_release }} {{ frr_apt_release }}" |       |

Dependencies
------------

N/A

Example Playbook
----------------

```yaml
- hosts: all
  roles:
    - { role: frr }
  vars:
    frr_config_eigrp_raw: |
      router eigrp 64512
        network 192.0.2.0/24
```

License
-------

BSD
