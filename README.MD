Ansible CMDB output to Dokuwiki
============================

This ansible playbook can be used to create a <a href="https://en.wikipedia.org/wiki/Configuration_management_database" class="icon-link">CMDB</a> using <a href="https://www.dokuwiki.org/dokuwiki" class="icon-link">dokuwiki</a> as your documentation platform.

----------

Workings
-----------

The templates in dokuwiki_templates are filled with ansible facts, combined with data gathered locally via <a href="http://docs.ansible.com/ansible/slurp_module.html" class="icon-link">slurp</a> from each system.
The data on each system is:
 - /root/description.txt 
 - /root/notes.txt 
 - /root/changelog.txt

The playbook creates these files when they are not already on every server so people can manage these locally.


> **Note:**

> - Please leave the settings in the yaml file on 'force: no', as if it is set to yes, the files will always be overwritten by defaults, thus destroying any data written into these.

Files
------
#### <i class="icon-file"></i> dokuwiki_templates/description.txt

This is a general information file for each server.
In our case we placed a dutch template containing the owner, location, function and SLA of each server in dokuwiki table format.

#### <i class="icon-folder-open"></i> dokuwiki_templates/serverlist.txt.j2

This is the index file containing a list of all servers with links to the 'per server' document.

> **Note:**

> - In our case, the destionation is start.txt.. please change it if you do NOT wish that you're dokuwiki index is overwritten.

