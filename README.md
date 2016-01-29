[![Build Status](https://travis-ci.org/ike-jp/ansible-role-anyenv.svg?branch=master)](https://travis-ci.org/ike-jp/ansible-role-anyenv)

Ansible Role: anyenv
=========

Under development


Requirements
------------

+ RedHat/CentOS: bash
+ Debian/Ubuntu: bash


Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

```
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

    - hosts: servers
      roles:
         - { role: ike-jp.anyenv }


License
-------

MIT License


Acknowledgments
---------------

I want to thank [Jeff Geerling](http://www.jeffgeerling.com/) and [YAEGASHI Takeshi](https://github.com/yaegashi)


Author Information
------------------

This role was created in 2.16 by ike-jp.

