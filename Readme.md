# Setting up devstack all in one

Ansible playbook to setup devstack on ubuntu 14.04 LTS

  - Prepares the system for devstack
  - Requires ubuntu 14.04 LTS
  - Need a non-root user to execute the ansible task with sudo priviledges

You can also:
  - specify the list of target hosts to be prepared for devstack
  - Specify which build of devstack to be installed
  - specify the local.conf file for your custom devstack setup 
  - Specify your favourite packages to be installed

```sh
ansible-playbook -i inventory/local -u stack --ask-pass --ask-sudo-pass -e "branch=stable/newton" site.yml
```

In above command
 - inventory/local ---> list of target host ip 
 - stack ---> non root user present on ubuntu 14.04
 - stable/newton ---> devstack branch to be cloned.

### Setup steps
  -- Update the inventory/local file with the target host ip address
  -- Update the roles/common/templates/localrc.sample for your spcecific configuration of devstack
 -- choose the devstack build and specifcy on the command (above as  ``` "stable/newton" ``` )
 -- Run the ansible command spcificying non-root user (above as ``` stack ``` )
 -- Wait for playbook to finish, ``` devstack```  folder would be present on ``` stack ``` user home directory
-- run stack.sh to continue with devstack
