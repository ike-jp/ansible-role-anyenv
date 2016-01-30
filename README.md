[![Build Status](https://travis-ci.org/ike-jp/ansible-role-anyenv.svg?branch=master)](https://travis-ci.org/ike-jp/ansible-role-anyenv)

Ansible Role: anyenv
=========

Under development


Requirements
------------

+ RedHat/CentOS: bash, git
+ Debian/Ubuntu: bash, git


Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

```yaml
anyenv:
  repository_url : https://github.com/riywo/anyenv
  install_dir: ~/.anyenv

  export: true
  profile_to_add_path: ~/.bashrc
  export_text: |
    if [ -d $HOME/.anyenv ] ; then
        export PATH="$HOME/.anyenv/bin:$PATH"
        eval "$(anyenv init -)"
    fi

  envs:
    - name: rbenv
      global: 2.3.0
      dependencies: []
      installation_versions:
        - 2.3.0
        - 2.2.4
...
```


Dependencies
------------

+ yaegashi.blockinfile


Example Playbook
----------------

```yaml
    - hosts: servers
      roles:
         - { role: ike-jp.anyenv }
```


License
-------

MIT License


Author Information
------------------

This role was created in 2016 by ike-jp.

[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/ike-jp/ansible-role-anyenv/trend.png)](https://bitdeli.com/free "Bitdeli Badge")


