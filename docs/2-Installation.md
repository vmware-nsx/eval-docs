
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
	  <img width=25% height=25% src="/docs/assets/Graphics/2.2.step1.jpg">
	</p>

- Select OVF file.  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step2.jpg">
	</p>

- Enter NSX-T Manager VM name + vCenter folder for VM.  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step3.jpg">
	</p>

- Select ESXi to host NSX-T Manager.  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step4.jpg">
	</p>

- Review NSX-T Manager VM details.  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step5.jpg">
	</p>

- Select NSX-T Manager VM size (Small).  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step6.jpg">
	</p>

- Select storage for NSX-T Manager VM.  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step7.jpg">
	</p>

- Select VDS Port Group for NSX-T Manager management vNIC (vCenter Managament Port Group).  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step8.jpg">
	</p>

- Enter NSX-T Manager information (passwords, hostname, IP, DNS, NTP). Important: Rolename is "NSX Manager".  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step9.jpg">
	</p>

- Review NSX-T Manager VM settings.  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step10.jpg">
	</p>

- Once NSX-T Manager deployment is finished, start the VM.  
	<p align="center">
	  <img width=40% height=40% src="/docs/assets/Graphics/2.2.step11.jpg">
	</p>
</details>


#### 3. Register NSX-T to vCenter
<details>
<summary>"Click to expand"</summary>

- Log on NSX-T Manager UI.  
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.3.step1.jpg">
	</p>

- Configuration NSX-T Licence.  
Under "System - Settings - Licenses", click "Add".  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.3.step2.jpg">
	</p>


- Register NSX-T in vCenter (to allow the deplyment of NSX elements into vCenter/ESXi from NSX).  
Under "System - Configuration - Fabric - Compute Managers", click "Add".  
	<p align="center">
	  <img width=50% height=50% src="/docs/assets/Graphics/2.3.step3a.jpg">
	</p>  
	<p align="center">
	  <img width=40% height=40% src="/docs/assets/Graphics/2.3.step3b.jpg">
	</p>

- Validate NSX-T registration in vCenter.  
Under "System - Configuration - Fabric - Compute Managers", click "Refresh" (bottom-left).
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.3.step4.jpg">
	</p>

</details>


#### 4. ESXi Host Preparation
<details>
<summary>"Click to expand"</summary>

##### Uplink Profile Creation

- Create Uplink Profile for Transport Nodes (Configuration of "VLAN-Overlay + NIC" for ESXis + Edge Node).  
Under "System - Configuration - Fabric - Profiles - Uplink Profiles", click "Add".  
See top graphic for VLAN for Overlay traffic (12) and number of uplinks for "VDS - NSX-T prepared" (1 NIC).  
  	<p align="center">
	  <img width=50% height=50% src="/docs/assets/Graphics/2.4.step1.jpg">
	</p>  

- Configure NSX-T for ESXi. Under "System - Configuration - Fabric - Node - Host Transport Nodes - Managed by", select "Lab-vCenter".  
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.4.step1.jpg">
	</p>
  - Configure each ESXi 


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


