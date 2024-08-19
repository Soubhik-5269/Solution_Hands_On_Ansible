Problem Statement :

--------------------------------------------------------------------------------------------------------

Install ansistrano.rollback using requirements.yml, add an entry inside it

Install the role on the local terminal using ansible-galaxy

Create The rollback playbook add the rollback role inside it

from deploy.yml copy parameters required for rollback file

Now use ansible playbook for rollback mechanism to be applied

----------------------------------------------------------------------------------------------------------

Solution:
-----------------------------------------------------------
Install the role on the local terminal using ansible-galaxy ----->
-----------------------------------------------------------

For this part we have to run follwing command:-

ansible-galaxy install ansistrano.deploy ansistrano.rollback


explanation:

The Directory structure for the file which has to be deployed from control server to the target server will be look like

    /var/www/myapp
    --------------
        |
        |-----index.html
        |

Then we have to follow this steps:

1. copy the content of index_v1.html and paste it in /var/www/myapp/index.html

2. Run deploy.yaml playbook using the following command

   ansible-playbook deploy.yml

   NOTE:- 1. Assuming default inventory file details already mentioned in ansible.cfg
          2. nginx service already installed and in started state in target machine 
          


3. Now Lets check in target machine web browser, we can see the content of index_v1.html in the browser for the myapp application
   In target machine the dir structure will be look like

   /var/www/mytarget/
   ------------------
   |
   |---current
   |    |
   |    |--myapp/index.html
   |---releases
   |    |
   |    |----{{current_version}}
   |    
   |---shared
   |

4. Now we have copy index_v2.html  and paste it in /var/www/myapp/index.html

5. Run deploy.yaml playbook using the following command

   ansible-playbook deploy.yml

   NOTE:- 1. Assuming default inventory file details already mentioned in ansible.cfg
          2. nginx service already installed and in started state in target machine

6. Now Lets check in target machine web browser, we can see the content of index_v1.html in the browser for myapp application
   In target machine the dir structure will be look like

   /var/www/mytarget/
   ------------------
   |
   |---current
   |    |
   |    |--myapp/index.html
   |---releases
   |    |
   |    |----{{current_version}}
   |    |----{{Previous_Version}}
   |    
   |---shared
   |

7. Now Lets run rollback.yaml file, Now If we check in the taret machine the content of myapp application will 
   be reverted back to index_v1.html 


