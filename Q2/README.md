Problem Statement :

--------------------------------------------------------------------------------------------------------

Create playbook boilerplate, YAML file

Change password for the user account, Create and configure and deploy user account,Configure
Public Key Authentication for deployed account

Add deployed user to sudoers, run updates and upgrades

Use "ufw" for iptables configuration,allow only "ssh" traffic

Configure "Postfix" to relay daily summary email with "debconf" module

Customize the ssh_port variable, disable ssh for root account

----------------------------------------------------------------------------------------------------------

Solution:

Run main.yml file from control server using the following command

ansible-playbook main.yml

Note: 1. Assuming the default inventory file already configured in ansible.cfg and the target server
         details already mentioned in default inventory file 


        for setting default inventory file we have to add following details in ansible.cfg

        [defaults]
        inventory=myinventory.ini
       

       For adding entry of target server, We have to add following details in myinventory.ini

       Test_Server ansible_host=192.168.100.5 ansible_user=MyUserName

