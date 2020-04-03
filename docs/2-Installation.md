
## Installation

### Table of Contents  
- [Validation of pre-requirements](#validation-of-pre-requirements)  
  - [Compute & Storage](#Compute--Storage)  
  - [Networking](#Networking)  
- [Installation of NSX-T](#Installation-of-NSX-t)  

---
---


### Validation of pre-requirements


#### Compute & Storage

<p align="center">
  <img width=75% height=75% src="/docs/assets/Graphics/2.1.Pre-Req Compute.jpg">
</p>

| Compute                   | Number        | Version   | Download |
|:--------------------------|:-------------:|:---------:|:--------:|
| vCenter                   | 1             | 7.0       | [download link](https://my.vmware.com/en/web/vmware/info/slug/datacenter_cloud_infrastructure/vmware_vsphere/7_0)     |
| vCenter-Cluster           | 1+            | n/a       | n/a      |
| ESXi per Cluster          | 2+            | 7.0       | [download link xxx](https://my.vmware.com/en/web/vmware/info/slug/networking_security/vmware_nsx_t_data_center/2_x)     |
| CPU per ESXi              | 8+            | n/a       | n/a      |
| RAM per ESXi              | 64GB+         | n/a       | n/a      |
| NIC per ESXi              | 2+            | n/a       | n/a      |

| Storage        | Shared storage - Recommended for live vMotion tests |
|:---------------|:---------------------------------------------------:|
| Size           | xxx GB                                              |


#### Networking

xxx Add picture 

| VLAN       | Number    | Description                                         |
|:-----------|:---------:|:----------------------------------------------------|
| Management | VLAN 10   | VLAN where Management is running (vCenter / ESXi-Mgt / future NSX-Mgr / future EdgeNode-Mgt) |
| Web        | VLAN 20   | VLAN where Web VMs will run (for Security only test) |
| Overlay    | VLAN 30   | VLAN where future NSX Logical Switches Overlay will run in |
| External   | VLAN 40   | VLAN where future NSX Logical Router will connect to provide "North/South" or "Logical/Physical" connectivity |


| Physical Router |                                                     |
|:----------------|:----------------------------------------------------|
| Interface       | 1 interface on each of those VLAN                   |
|                 | *Note: Since overlay will run only in VLAN30, there is no need to enable large MTU on router interface* |



---
---

### Installation of NSX-T
xxx To Do

xxx Add picture with NSX in ESXi + IP@ of everything (Mgt ESXi + NSX-Mgr Mgt + ESXi-TEP + Edge Node VM + Mgt IP + TEP IP)

- [Download of NSX Manager OVA](#Download-of-NSX-Manager-OVA)
- [Deployment of NSX-T Manager](#Deployment-of-NSX-T-Manager)
- [Register NSX to vCenter](#Register-NSX-to-vCenter)
- [ESXi Host Preparation](#ESXi-Host-Preparation)
  - [Uplink Profile Creation](#Uplink-Profile-Creation)
  - [Installion of NSX in ESXi](#Installion-of-NSX-in-ESXi)
- [Deployement of Edge Node (not required for the "Security only" tests)](#Deployement-of-Edge-Node)
  - [Creation of VDS Port Group "All VLAN"](#creation-of-vds-port-group-all-vlan)
  - [Installation of NSX Edge Node](#Installation-of-NSX-Edge-Node)

#### Download of NSX Manager OVA


#### Deployment of NSX-T Manager


#### Register NSX to vCenter


#### ESXi Host Preparation

##### Uplink Profile Creation

##### Installion of NSX in ESXi


#### Deployement of Edge Node

##### Creation of VDS Port Group "All VLAN"

##### Installation of NSX Edge Node
