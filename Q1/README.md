Problem Statement :

--------------------------------------------------------------------------------------------------------

Run preboot tasks,use "yum" for upgrades

Use Command module to "reboot" server

Run "wait_for" module to wait for 300 seconds for port 22 to become available-before resuming
the playbook.The port number can be changed if it is not SSH

Resume playbook on response from 22

----------------------------------------------------------------------------------------------------------