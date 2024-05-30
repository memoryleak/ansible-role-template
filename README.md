memoryleak.template
===================

Template role to base new roles on. A docker based molecule setup is configured. The role includes before any other step system specific variables, sets facts and includes tasks.

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

Molecule
--------
    poetry install
    molecule test

License
-------
MIT

Author Information
------------------
Haydar Ciftci <haydar.ciftci@gmail.com>
