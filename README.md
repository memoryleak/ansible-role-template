memoryleak.template
===================

Template role to base new roles on. The tasks and variable files are included in the following order:

	vars/*-[Linux|Darwin|...].yml
	vars/*-[RedHat|Debian|...].yml
	vars/*-[Fedora|CentOS|...].yml
	
	tasks/*-[Linux|Darwin|...].yml
	tasks/*-[RedHat|Debian|...].yml
	tasks/*-[Fedora|CentOS|...].yml
	

Requirements
------------

None

Role Variables
--------------

None

Dependencies - PIP
------------------

	ansible
	docker
	molecule[docker]

Dependencies - Packages
-----------------------

	docker

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: memoryleak.template }

Testing
-------

Setup:
------
    virtualenv .venv
    source .venv/bin/activate
    pip install -r requirements.txt
	sudo dnf install docker ansible python3-molecule python3-molecule-docker

Execution:
----------
	
	molecule converge

License
-------

MIT

Author Information
------------------

Haydar Ciftci <haydar.ciftci@gmail.com>
