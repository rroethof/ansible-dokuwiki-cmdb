Ansible CMDB output to Dokuwiki
============================

This ansible playbook can be used to create a <a href="https://en.wikipedia.org/wiki/Configuration_management_database" class="icon-link">CMDB</a> using <a href="https://www.dokuwiki.org/dokuwiki" class="icon-link">dokuwiki</a> as your documentation platform.

----------

Workings
-----------

The templates in dokuwiki_templates are filled with ansible facts, combined with data gathered locally via <a href="http://docs.ansible.com/ansible/slurp_module.html" class="icon-link">slurp</a> from each system.
The variables are:

> - dokuwiki_user: dokuwiki
>   This is the user that runs dokuwiki on your wiki server

> - dokuwiki_group: dokuwiki
>   This is the group that runs dokuwiki on your wiki server

> - dokuwiki_local_destination: /root/.documentation
>   The location of the local documentation on each server

> - dokuwiki_local_destination_user: root
>   The user of the documentation on each server

> - dokuwiki_local_destination_group: root
>   The user of the documentation on each server

> - dokuwiki_directory: /home/dokuwiki/html/data/pages/serverlijst
>   The directory of your dokuwiki data

> - dokuwiki_serverlist_destination: /home/dokuwiki/html/data/pages/start.txt
>   The inventory page location of your dokuwiki

> - dokuwiki_targetserver: monitor.familieroethof.nl
>   The dokuwiki server

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

TODO
------

Obviously every project still has things that need to be fixed or new wishes.

 - Some servers (clients of my work) don't have curl, therefore the index has an issue, need to fix that
 - Need to build a filter for local addressess i.e. 127.* or fe80::
 - Mountpoints json needs to be 'de jsonned' to table format
 - Need to get network interfaces overview
 - etc.

If you have any need or request, please state so in the issue list.

