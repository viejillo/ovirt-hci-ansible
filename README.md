Hyperconverged Infrastructure with oVIrt and Gluster storage.


hc-ansible-deployment is end-to-end HC deployment playbook which is using both gluster-ansible role and ovirt-ansible-hosted-engine-setup role.

1. There is one inventory file which is gluster_inventory.yml has gluster related configurations.
   Enable "VDO config" for VDO and disable Non-VDO part.
2. The json file he_gluster_vars.json has Hosted-Engine related configurations for gluster.

For new HC deployment both files need to be modified with accurate values like host,device,pvs,vgs,lvs,fqdn,passwords etc

How to run:
 > cd /etc/ansible/roles/gluster.ansible/playbooks/hc-ansible-deployment

 >> ansible-playbook -i gluster_inventory.yml hc_deployment.yml --extra-vars='@he_gluster_vars.json'

For gluster deployment clean up:
 >cd /etc/ansible/roles/gluster.ansible/playbooks/hc-ansible-deployment
 >> ansible-playbook -i gluster_inventory.yml tasks/gluster_cleanup.yml

Note: Replace appropriate host name with host1,host2 and host3 in inventory file (gluster_inventory.yml) and json file (he_gluster_vars.json).

Other information:
1.-Deployed the servers using oVirt 4.3.7 image.
2.-Added ssh keys to be able to ssh from host 1 over to host 2 and host 3
