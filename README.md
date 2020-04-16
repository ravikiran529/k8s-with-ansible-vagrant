# k8s-with-ansible-vagrant

This is to spin-up kubernetes cluster with Vagrant and Ansible provisioning.
You need to have ==> virtualization software like VirtualBox,VM Ware etc.,In my case it is VirtualBox. 
                 ==> Virtualization automation software - Vagrant
                 
Note: You don't need to install ansible in the host machine as it uses "ansible_local" as provisioning option. 
      ( Mostly helpful in case you are on windows )
    
 master 192.168.50.10 (ansible controller)
 node-1 192.168.50.11
 node-2 192.168.50.12
 
----------------------------------------------------------------------
Just 3 commands to get all the setup within minutes 
----------------------------------------------------------------------

$ vagrant up 
 ------------
  This will run 3 virtual machines ( master, node-1, node-2 ) and use master as a ansible controller machine & k8s master as well.
  
$ vagrant ssh master
 -------------------
  To get into the master machine.
  
$ kubectl get nodes
 ------------------
  To get nodes in the k8s cluster
