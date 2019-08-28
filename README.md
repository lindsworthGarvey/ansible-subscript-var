ansible-subscript-variable
----------------------
Playbook provides an example of how to access variables using ansible subscript style


Variable Definition:
----------------------
---
host:
  ip:
    - 10.13.3.10
    - 10.13.3.11
    - 10.13.3.12
  name:
   - k8s-etcd.curbstoneops.com
   - k8s-etcd-1.curbstoneops.com
   - k8s-etcd-2.curbstoneops.com

Example:
----------------------
Use debug to display the derived variable - comprised of subscript elements

- debug:
    msg="{{ host['ip'][0] }} {{ host['name'][0] }}"

Will return:

TASK [../roles/test : debug]
*************************************************************************************
ok: [localhost] => {
    "msg": "10.13.3.10 k8s-etcd.curbstoneops.com"
}

Testing locally
----------------------
ansible-playbook -c local -i ./hosts  ./playbooks/main.yml
