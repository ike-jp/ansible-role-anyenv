[![Build Status](https://travis-ci.org/ike-jp/ansible-role-anyenv.svg?branch=master)](https://travis-ci.org/ike-jp/ansible-role-anyenv)

Ansible Role: anyenv
=========

Installs anyenv on RHEL/CentOS/Debian/Ubuntu.


Requirements
------------

+ RedHat/CentOS: /bin/bash, git
+ Debian/Ubuntu: /bin/bash, git


Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

```yaml
anyenv_repository_url: https://github.com/riywo/anyenv
anyenv_installaton_dir: ~/.anyenv

anyenv_export: true
anyenv_export_profile_to_add_path: ~/.bashrc
anyenv_export_block: |
  if [ -d $HOME/.anyenv ] ; then
      export PATH="$HOME/.anyenv/bin:$PATH"
      eval "$(anyenv init -)"
  fi

...

anyenv_envs:
  - name: rbenv
    global_version: 2.3.0
    installation_versions:
      - 2.3.0

  - name: pyenv
    global_version: 2.7.10
    installation_versions:
      - 2.7.10
      - 3.5.1
...
```


Installation
------------

```shell
$ cd roles
$ git clone https://github.com/ike-jp/ansible-role-anyenv.git ike-jp.anyenv
```


Dependencies
------------

+ yaegashi.blockinfile


Example Playbook
----------------

```yaml
    - hosts: servers

      vars:
        anyenv_envs:
          - name: rbenv
            global_version: 2.3.0
            installation_versions:
              - 2.3.0

          - name: pyenv
            global_version: 2.7.10
            installation_versions:
              - 2.7.10
              - 3.5.1

        anyenv_dependencies:
          - name: common
            libraries:
              - zlib1g-dev

          - name: rbenv
            libraries:
              - sqlite3
              - libsqlite3-d
              - ...

          - name: pyenv
            libraries:
              - libbz2-dev
              - ...
...
      roles:
         - { role: ike-jp.anyenv }
```


TODO
----

+ Check installed versions and global.


License
-------

MIT License


Author Information
------------------

This role was created in 2016 by ike-jp.



[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/ike-jp/ansible-role-anyenv/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

