memoryleak.template
===================

Template role to base new roles on.

Requirements
------------

None

Role Variables
--------------

None

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: memoryleak.template }

Testing
-------

Setup:

    virtualenv .venv
    source .venv/bin/activate
    pip install -r requirements.txt

Execution:
	
	molecule test

License
-------

MIT

Author Information
------------------

Haydar Ciftci <haydar.ciftci@gmail.com>
