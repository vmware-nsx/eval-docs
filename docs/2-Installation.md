
## 2. Installation of NSX-T

### Table of Contents  
- [Download of NSX Manager OVA](#Download-of-NSX-Manager-OVA)
- [Deployment of NSX-T Manager](#Deployment-of-NSX-T-Manager)
- [Register NSX to vCenter](#Register-NSX-to-vCenter)
- [ESXi Host Preparation](#ESXi-Host-Preparation)
  - [Uplink Profile Creation](#Uplink-Profile-Creation)
  - [Installion of NSX in ESXi](#Installion-of-NSX-in-ESXi)
- [Deployement of Edge Node (not required for the "Security only" tests)](#Deployement-of-Edge-Node)
  - [Creation of VDS Port Group "All VLAN"](#creation-of-vds-port-group-all-vlan)
  - [Installation of NSX Edge Node](#Installation-of-NSX-Edge-Node)

---


xxx To Do

<p align="center">
  <img width=75% height=75% src="/docs/assets/Graphics/2.1.Installation-Design.jpg">
</p>


| IP of each Element        | Management    | Overlay       |
|:--------------------------|:-------------:|:-------------:|
| vCenter                   | 19.168.50.4   | -             |
| ESXi1                     | 19.168.50.21  | 192.168.51.21 |
| ESXi2                     | 19.168.50.22  | 192.168.51.22 |
| NSX-T Manager             | 19.168.50.5   | -             |
| Edge Node                 | 19.168.50.31  | 192.168.51.31 |




#### Download of NSX Manager OVA
<details>
<summary>"Click to expand"</summary>
Download NSX-T 3.0 Manager for VMware ESXi OVA file [here](https://my.vmware.com/en/web/vmware/info/slug/networking_security/vmware_nsx_t_data_center/2_x)

xxx fix the link + add screenshot of VMware download.
</details>


#### Deployment of NSX-T Manager
<details>
<summary>"Click to expand"</summary>

From vCenter, deploy NSX-T Unified Appliance OVA.
xxx Add the screenshots


</details>


#### Register NSX to vCenter
<details>
<summary>"Click to expand"</summary>

From NSX-T Manager under "xxx - xxx", register vCenter.
xxx Add the screenshots

</details>


#### ESXi Host Preparation
<details>
<summary>"Click to expand"</summary>

##### Uplink Profile Creation

From NSX-T Manager under "xxx - xxx", create Uplink Profile for Transport Nodes (ESXi + Edge Node):
- VLAN information for Overlay traffic (= VLAN 12 in lab)
- Number of NIC for "VDS - NSX-T prepared" switch (= 1 NIC in lab)
xxx Add the screenshots


##### Installion of NSX in ESXi

From NSX-T Manager under "xxx - xxx", install NSX-T in the ESXi.
xxx Add the screenshots


</details>


#### Deployement of Edge Node
<details>
<summary>"Click to expand"</summary>

##### Creation of VDS Port Group "All VLAN"
From vCenter, create a Port Group "All VLAN" (= VLAN Tag 1-4096).
xxx Add the screenshots

##### Installation of NSX Edge Node
From NSX-T Manager, deploy 1 Edge Node + configure it.
xxx Add the screenshots

</details>


