# Ansible Collection - dholzer.vmware_vcda

Documentation for the collection.

# vcda.yml
```
vcda:

  deployment:
    vce:
      hostname: 'base01-vce-01.vcloud24.net'
      username: 'administrator@vsphere.local'
      password: 'VMwareVCE1.'
    
    ova: 'VMware-Cloud-Director-Availability-Provider-4.5.0.5855303-21231906fd_OVF10.ova'

    datacenter: 'base01'
    folder: '/vcd01'
    # to cluster 'base01'
    # to resource pool 'base01/Resources/vcd01'
    cluster: 'base01/Resources/vcda'

    datastore: 'qnap-ts879 vmw_vsphere'


  domain: vcloud24.net
  search_domain: vcloud24.net
  dns: 172.16.0.1
  ntp: 172.16.0.1

  check_pattern: "VMware Cloud Director Availability" 
  
  manager:
    - name: psrv01cam001
      role: cloud
      root_password: VMwareVCDA1.
      disk_provisioning: 'thin'
      network: 'base01-0101mgmt'
      ssh_enabled: true
      ip: 172.16.0.14
      netmask_cidr: 26
      gateway: 172.16.0.1
      #mtu:
      #deployment:

  replicator:
    - name: psrv01car001
      role: replicator
      root_password: VMwareVCDA1.
      disk_provisioning: 'thin'
      network: 'base01-0101mgmt'
      ssh_enabled: true
      ip: 172.16.0.15
      netmask_cidr: 26
      gateway: 172.16.0.1
      #mtu:
      #deployment:

  tunnel:
    - name: psrv01cat001
      role: tunnel
      root_password: VMwareVCDA1.
      disk_provisioning: 'thin'
      network: 'base01-0101mgmt'
      ssh_enabled: true
      ip: 172.16.0.16
      netmask_cidr: 26
      gateway: 172.16.0.1
      #mtu:
      #deployment:
```

# site.yml
```
---
# Deploy
- hosts: localhost
  gather_facts: false
  collections:
    - dholzer.vmware_vcda
  
  roles:
    - vcda_deploy
```