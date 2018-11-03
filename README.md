[![Build Status](https://travis-ci.org/kurrier/ansible-role_packages.svg?branch=master)](https://travis-ci.org/kurrier/ansible-role_packages)

Ansible Role: packages
=========

RHEL Package Management

Requirements
------------

N/A

Role Variables
--------------
* packages_function_check: [true/false] - enable/disable Update Report function
* packages_function_install: [true/false] - enable/disable Install package function
* packages_function_update_all: [true/false] - enable/disable Update All packages function
* packages_function_update_advisory: [true/false] - enable/disable Advisory Update function
* packages_function_remove: [true/false] - enable/disable Remove Pakages
* packages_security_remove: [true/false] - enable/disable Critical Updates Only

## Run ##
* packages_check: [true] - run Update Report
* packages_advisory: [Advisory ID] - install RHEL Advisory
* packages_all: [true] - install all Updates
* packages_install: [package1, package2] - install/update certain packages
* package_remove: [package] - uninstall certain packages
* package_remove_job: [UUID] - undo yum install by UUID produced by install/update process

## Misc Settings ##

* packages_reboot: [true/false] - enable/disable auto Reboot in Update All

* packages_function_report: [true/false] - enable/disable Reports
* packages_function_alert: [true/false] - enable/disable Alerts

* ansible_archive_host: localhost - Host to store reports
* ansible_archive_user: someone - SSH user that has access to ansible_report_location


Dependecies
-----------

None

Example Playbook
----------------
        - hosts: localhost
          vars:
            packages_function_check: false
        packages_function_install: true
        packages_function_update_all: false
        packages_function_update_advisory: true
        packages_function_alert: true

        packages_advisory: RHSA-2017:2459
        packages_install: screen

    - role: lc.packages

This will install advisory and install screen.

Test
----------------

ansible-playbook tests/test.yml -i tests/inventory

Plans
----------------
- Add support for Ubuntu/Debian

License
-------

Licensed under GPLv3 License. See LICENSE for details.

Author Information
------------------

Nick Lalumiere
