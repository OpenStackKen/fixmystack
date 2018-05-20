
# Turn off Ansible host key checking
export ANSIBLE_HOST_KEY_CHECKING=False

/lab-environment
ansible-playbook -i hosts target-create.yml
ansible-playbook -i hosts admin-create.yml
ansible-playbook -i hosts base-users.yml

/rpcv12-cloud-regionA
ansible-playbook -i hosts all.yml
ansible-playbook -i hosts prep_deploy.yml
ansible-playbook -i hosts build.yml


ansible allinone -m shell -a "tail -n 35 /var/log/ansible/ansible.log" -i hosts -u root
