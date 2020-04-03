
## Installation

##### Table of Contents  
- [Validation of pre-requirements](2-Installation.md#validation-of-pre-requirements)  
  - [Compute & Storage](2-Installation.md#Compute--Storage)  
  - [Networking](2-Installation.md#Networking)  
- [Installation of NSX](2-Installation.md#Installation-of-NSX)  

### Validation of pre-requirements


#### Compute & Storage

<p align="left">
  <img width=75% height=75% src="/docs/assets/Graphics/2.1.Pre-Req Compute.jpg">
</p>

| Compute                   | Number        | Version   | Download |
|:--------------------------|:-------------:|:---------:|:--------:|
| vCenter                   | 1             | 7.0       | [download link](https://my.vmware.com/en/web/vmware/info/slug/datacenter_cloud_infrastructure/vmware_vsphere/7_0)     |
| vCenter-Cluster           | 1+            | n/a       | n/a      |
| ESXi per Cluster          | 2+            | 7.0       | [download link xxx](https://my.vmware.com/en/web/vmware/info/slug/networking_security/vmware_nsx_t_data_center/2_x)     |
| NIC per ESXi              | 2+            | n/a       | n/a      |

| Storage        | Shared storage - Recommended for live vMotion tests |
|:---------------|:---------------------------------------------------:|
| Size           | xxx GB                                              |


#### Networking

xxx Add picture 

- VLAN
  - Management (VLAN10) <--- VLAN where Management is running (vCenter / ESXi-Mgt / future NSX-Mgr / future EdgeNode-Mgt)
  - Web (VLAN20)        <--- VLAN where Web VMs will run (for Security only test)
  - Overlay (VLAN30)    <--- VLAN where future NSX Logical Switches Overlay will run in
  - External (VLAN40)   <--- VLAN where future NSX Logical Router will connect to provide "North/South" or "Logical/Physical" connectivity

- Physical Router
  - configure 1 interface on each of those VLAN
  Note: Since overlay will run here only in VLAN30, there is no need to enable large MTU on router interface



---

### Installation of NSX
xxx To Do
- Download NSX Manager OVA [download link xxx]
- Deplp


