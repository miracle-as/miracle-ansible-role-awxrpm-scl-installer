# miracle-ansible-role-awxrpm-scl-installer


**roles/requirements.yml
**
---
roles:
  - src: https://github.com/JakobHolstDK/miracle-ansible-role-awxrpm-scl-installer.git
    scm: git
    version: "master"

ansible-galaxy install -fr roles/requirements.yml 



**playbook_setupawx.yml
**
- name: Ping server
  hosts: awxrpm

  tasks:
  - name: Example from an Ansible Playbook
    ansible.builtin.ping:

  - name: Build the awx service
    vars:
       selinuxstate: "permissive"
       awx_log_path: "/home/consul/log"
       postgresqlversion: "10"
       awx_db_password: "JASDJASD"
       awxpassword: "kfssdf"
       postgreshost: "127.0.0.1"
       nginx_disable_https: "true"
       nginx_http_port: 80
       nginx_disable_hsts: "false"
       nodejsversion: "16"
       secret_key: "ijpjgb4di)quze^0y5-6m6+#n*9)uf&k-0%lin)2d$e%%mufam"
       CLUSTER_HOST_ID: "demoawx01"
       awx_install_redis_init_name:
    include_role:
       name:  miracle-ansible-role-awxrpm-scl-installer

inventory.sh is a script that returns inventory.json
(for virt-lightning you can use:

**inventory/inventory.sh 
**
#!/usr/bin/env bash
vl ansible_inventory > inventory.ini
ansible-inventory --inventory inventory.ini --list

**Run the playbook
**

ansible-playbook -i inventory/inventory.sh pb_awx.yml

