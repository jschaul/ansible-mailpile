Ansible-Mailpile
=========

Installs Mailpile, see [https://mailpile.is]() for more information.

Included is a vagrant file. If you wish to get Mailpile up and running in a virtual machine, just make sure you have [vagrant](https://www.vagrantup.com/) installed, then proceed as follows:

    git clone https://github.com/jschaul/ansible-mailpile.git
    cd ansible-mailpile
    vagrant up
    # go get a drink, this can take some time depending on your internet speed...

    # start mailpile:
    vagrant ssh -c "cd /home/vagrant/mailpile && ./mp --www=0.0.0.0:33411 --wait"

Tested with:

* Vagrant 1.6.5
* ansible 1.7.2


Requirements
------------

None

Role Variables
--------------

Variables you can override with their defaults:

    mailpile_user               : "{{ansible_env.SUDO_USER}}"
    mailpile_owner              : "{{mailpile_user}}"
    mailpile_group              : "{{mailpile_user}}"
    mailpile_version            : "release/beta"
    mailpile_home_directory     : "/home/{{mailpile_user}}"
    mailpile_working_directory  : "{{mailpile_home_directory}}/mailpile"

Dependencies
------------

None

Example Playbook
----------------

    - hosts: all
      sudo: True
      vars:
        - mailpile_version : "master"
      roles:
        - {role: "ansible-mailpile" }

License
-------

MIT
