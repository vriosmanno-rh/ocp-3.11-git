ocp-3.11-git
=========

An Ansible role to copy all required OCP 3.11 git repos to local disk for disconnected installation.

Requirements
------------

- Ansible >= 2.5
- RHEL == 7

Role Variables
--------------

| Parameter | Type | Required |  Default Value | Comments |
| --- | --- | --- | --- | --- |
| **content_sync_path** | string | yes | `/data` | The destination path for the openscap OVAL definitions |
| **github_repos** | list | yes | *see role defaults*  | List of github repos to pull in for OCP 3.11 |
| **temp_sync_path** | string | yes | `/tmp` | The temp path for the reposync files |

### If Running on a RHEL System these variables handle connecting to RHSM to install git
| Parameter | Type | Required | Default Value | Comments |
| --- | --- | --- | --- | --- |
| **rhsm_user** | string | no | *undefined* | The account username with access to subscriptions on https://access.redhat.com, **required only when running from a RHEL system** |
| **rhsm_password** | string | no | *undefined* | The account password with access to subscriptions on https://access.redhat.com, **required only when running from a RHEL system** |
| **rhsm_pool** | string | no | *undefined* | The subscription pool IDs to consume that contain OCP 3.11. (ex. `0123456789abcdef0123456789abcdef`), **only when running from a RHEL system** |

Examples
--------

### Running with defaults
```yaml
- name: ocp-3.11-containers example
  roles:
    - role: ocp-3.11-containers
      tags:
        - git-clone
```

### Running with different git repos
```yaml
- name: ocp-3.11-containers example
  roles:
    - role: ocp-3.11-containers
      tags:
        - git-clone
      vars:
        github_repos:
          - { branch: master, project: cakephp-ex, repo: sclorg }
```

License
-------

GPLv3
