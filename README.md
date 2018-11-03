# Ansible Role: packages

Install Packages

Requirements
------------

N/A

Role Base Variables
--------------
packages_check: [true] - run Update Report
packages_advisory: [Advisory ID] - install RHEL Advisory
packages_all: [true] - install all Updates
packages_install: [package1, package2] - install/update certain packages
package_remove: [package] - uninstall certain packages
package_remove_job: [UUID] - undo yum install by UUID produced by install/update process

Function Base Variables
--------------

packages_function_check: [true/false] - enable/disable Update Report function
packages_function_install: [true/false] - enable/disable Install package function
packages_function_update_all: [true/false] - enable/disable Update All packages function
packages_function_update_advisory: [true/false] - enable/disable Advisory Update function
packages_function_remove: [true/false] - enable/disable Remove Pakages

packages_reboot: [true/false] - enable/disable auto Reboot in Update All

packages_function_report: [true/false] - enable/disable Reports
packages_function_alert: [true/false] - enable/disable Alerts

packages_function_mail: [true/false] - enable/disable Email alerts
packages_function_slack: [true/false] - enable/disable Slack alerts

Extra Variables (Global recommended)
--------------
ansible_mail_host: localhost - Email host
ansible_mail_from: ansible@localhost - Email sender
ansible_mail_to: you@you.com - Email reciept

ansible_archive_host: localhost - Host to store reports
ansible_archive_user: someone - SSH user that has access to ansible_report_location

ansible_slack_token: xxx/yyy/zzz - Slack App API token
ansible_slack_channel: #mychannel - Slack Channel


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
		
		ansible_slack_token: xxx/yyy/zzz
		ansible_slack_channel: #mychannel
		
    - role: lc.packages
	
This will install advisory and install screen, then alert over Slack on success.

Test
----------------

ansible-playbook tests/test.yml -i tests/inventory

License
-------
GPLv3
