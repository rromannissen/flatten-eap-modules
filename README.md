Flatten EAP Modules
=========

This role flattens the whole modules directory structure to extract all JAR files for them to be analyzed by Red Hat Application Migration Toolkit. This whole thing could have been done with a simple find command if all JARs had a consistent versioning applied to its name, but we all know life sucks sometimes.

The role deals with repeated JAR names by adding a suffix with the corresponding slot to the name. For example, app.jar in slot directory 1.11 becomes app_1.11.jar in the target directory. This makes each file unique and avoids naming conflicts.

Requirements
------------

None

Role Variables
--------------
- *eap_modules_path*: Path to the modules directory to be flattened.
- *target_directory*: Directory to copy the renamed JARs to.


Dependencies
------------

None

Example Playbook
----------------

    - hosts: eap
      roles:
         - { role: flatten-eap-modules, eap_modules_path: "/opt/jboss/modules/custom", target_directory: "/tmp/flattened" }

License
-------

BSD
