
## 2. Installation of NSX-T

<p align="center">
  <img width=75% height=75% src="/docs/assets/Graphics/2.0.Installation-Design.jpg">
</p>


| IP of each Element        | Management    | Overlay       |
|:--------------------------|:-------------:|:-------------:|
| vCenter                   | 19.168.50.4   | -             |
| ESXi1                     | 19.168.50.21  | 192.168.51.21 |
| ESXi2                     | 19.168.50.22  | 192.168.51.22 |
| NSX-T Manager             | 19.168.50.5   | -             |
| Edge Node                 | 19.168.50.31  | 192.168.51.31 |

### Steps:

#### 1. Download of NSX Manager OVA
<details>
<summary>"Click to expand"</summary>

Download NSX-T 3.0 Manager for VMware ESXi OVA file [download link xxx](https://my.vmware.com/en/web/vmware/info/slug/networking_security/vmware_nsx_t_data_center/2_x)

xxx fix the link + add screenshot of VMware download.
</details>


#### 2. Deployment of NSX-T Manager
<details>
<summary>"Click to expand"</summary>

- From vCenter, deploy NSX-T Unified Appliance OVA.  
<p align="center">
  <img width=75% height=75% src="/docs/assets/Graphics/2.0.Installation-Design.jpg">
</p>


</details>


#### 3. Register NSX to vCenter
<details>
<summary>"Click to expand"</summary>

From NSX-T Manager under "xxx - xxx", register vCenter.  
xxx Add the screenshots

</details>


#### 4. ESXi Host Preparation
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


#### 5. Deployement of Edge Node
<details>
<summary>"Click to expand"</summary>

##### Creation of VDS Port Group "All VLAN"
From vCenter, create a Port Group "All VLAN" (= VLAN Tag 1-4096).  
xxx Add the screenshots

##### Installation of NSX Edge Node
From NSX-T Manager, deploy 1 Edge Node + configure it.  
xxx Add the screenshots

</details>


