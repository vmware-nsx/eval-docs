
## 2. Installation of NSX-T

*Disclaimer: The below install is a minimal installation intended for a lab environment only. We do not recommend below install in a live production environment.*

<p align="center">
  <img width=75% height=75% src="/docs/assets/Graphics/2.0.Installation-Design-1.jpg">
</p>  
<p align="center">
  <img width=75% height=75% src="/docs/assets/Graphics/2.0.Installation-Design-2.jpg">
</p>  


| IP of each Element | Management (VLAN11) | Overlay -TEP (VLAN12) |
|:-------------------|:-------------------:|:---------------------:|
| vCenter            |     19.168.50.4     |           -           |
| ESXi1              |    19.168.50.21     |     192.168.51.21     |
| ESXi2              |    19.168.50.22     |     192.168.51.22     |
| NSX-T Manager      |     19.168.50.5     |           -           |
| Edge Node          |    19.168.50.31     |     192.168.51.31     |

---

### Steps:

### 1. Download of NSX Manager OVA
<details>
<summary>"Click to expand"</summary>

Download NSX-T 3.0 Manager for VMware ESXi OVA file [download link ](https://my.vmware.com/web/vmware/details?downloadGroup=NSX-T-300&productId=982&rPId=45015)
<p align="center">
  <img width=75% height=75% src="/docs/assets/Graphics/2.1.step1.jpg">
</p>

*Note: NSX-T Evaluations are based on Limited export build (no IPSEC VPN, no HTTPS LB), with no transition path to the full version.*

</details>

---

### 2. Deployment of NSX-T Manager
<details>
<summary>"Click to expand"</summary>

- **From vCenter, deploy NSX-T Unified Appliance OVA.**  
	<p align="center">
	  <img width=25% height=25% src="/docs/assets/Graphics/2.2.step1.jpg">
	</p>

- **Select OVF file.**  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step2.jpg">
	</p>

- **Enter NSX-T Manager VM name + vCenter folder for VM.**  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step3.jpg">
	</p>

- **Select ESXi to host NSX-T Manager.**  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step4.jpg">
	</p>

- **Review NSX-T Manager VM details.**  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step5.jpg">
	</p>

- **Select NSX-T Manager VM size (Small).**  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step6.jpg">
	</p>

- **Select storage for NSX-T Manager VM.**  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step7.jpg">
	</p>

- **Select VDS Port Group for NSX-T Manager management vNIC (vCenter Managament Port Group).**  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step8.jpg">
	</p>

- **Enter NSX-T Manager information (passwords, hostname, IP, DNS, NTP). Important: Rolename is "NSX Manager".**  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step9.jpg">
	</p>

- **Review NSX-T Manager VM settings.**  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.2.step10.jpg">
	</p>

- **Once NSX-T Manager deployment is finished, start the VM.**  
	<p align="center">
	  <img width=40% height=40% src="/docs/assets/Graphics/2.2.step11.jpg">
	</p>
</details>

---

### 3. Register NSX-T to vCenter
<details>
<summary>"Click to expand"</summary>

*Note: NSX-T Manager requires few minutes to fully start and get all its services running.*

- **Log on NSX-T Manager UI.**  
In a browser: https://192.168.50.5/.  
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.3.step1.jpg">
	</p>

- **Configuration NSX-T Licence.**  
Under "System - Settings - Licenses", click "Add".  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.3.step2.jpg">
	</p>


- **Register NSX-T in vCenter (to allow the deplyment of NSX elements into vCenter/ESXi from NSX).**  
Under "System - Configuration - Fabric - Compute Managers", click "Add".  
	<p align="center">
	  <img width=50% height=50% src="/docs/assets/Graphics/2.3.step3a.jpg">
	</p>  
	<p align="center">
	  <img width=40% height=40% src="/docs/assets/Graphics/2.3.step3b.jpg">
	</p>

- **Validate NSX-T registration in vCenter.**  
Under "System - Configuration - Fabric - Compute Managers", click "Refresh" (bottom-left).
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.3.step4.jpg">
	</p>

</details>

---

### 4. ESXi Host Preparation
<details>
<summary>"Click to expand"</summary>

#### 4.1. New VDS-NSX creation

<details>
<summary>"Click to expand"</summary>

- **Create New VDS-NSX (for future NSX-T Logical Switches).**  
From vCenter, under "Networking", select the Data Center, and right-click to create a "New Distributed Switch".  
*For this lab, see the top of page for "Number of uplinks (1)",  
and "Default Port Group (none)".*  
  	<p align="center">
	  <img width=40% height=40% src="/docs/assets/Graphics/2.4.1.step1.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.4.1.step2.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.4.1.step3.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.4.1.step4.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.4.1.step5.jpg">
	</p>  

- **Add that VDS-NSX to ESXi.**  
From vCenter, under "Networking", select the VDS-NSX, and right-click to "Add and Manage Hosts...".  
  	<p align="center">
	  <img width=40% height=40% src="/docs/assets/Graphics/2.4.1.step6.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.4.1.step7.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.4.1.step8.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.4.1.step9.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.4.1.step10.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.4.1.step11.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.4.1.step12.jpg">
	</p>  

- **Configure that VDS-NSX with an large MTU (at least 1700).**  
From vCenter, under "Networking", select the VDS-NSX, and right-click to "Add and Manage Hosts...".  
  	<p align="center">
	  <img width=40% height=40% src="/docs/assets/Graphics/2.4.1.step13.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.4.1.step14.jpg">
	</p>  

</details>


#### 4.2. Uplink Profile Creation

<details>
<summary>"Click to expand"</summary>

- **Create Uplink Profile for Transport Nodes ("VLAN-Overlay + NIC" information for ESXis + Edge Node).**  
From NSX-T, under "System - Configuration - Fabric - Profiles - Uplink Profiles", click "Add".  
*For this lab, see the top of page for VLAN for Overlay traffic information (12),  
and number of uplinks for "VDS - NSX-T" information (1 NIC).*  
  	<p align="center">
	  <img width=50% height=50% src="/docs/assets/Graphics/2.4.2.step1.jpg">
	</p>  

</details>


#### 4.3. Installion of NSX in ESXi

<details>
<summary>"Click to expand"</summary>

- **Configure NSX-T for ESXi.**  
  - Select each ESXi of vCenter-Cluster  
  Under "System - Configuration - Fabric - Node - Host Transport Nodes - Managed by", select "Lab-vCenter".  
  *Select Type = VDS (to enable NSX into the existing "VDS-NSX" vCenter Distributed Switch),  
  Mode = Standard,  
  Transport Zone = "nsx-overlay-transportzone" (Default TZ for overlay traffic) + "nsx-vlan-transportzone" (Default TZ for VLAN traffic),  
  Uplink Profile = "Lab-HostProfile" (with VLAN-Overlay information),  
  IP (TEP) = Information on top of the page,  
  Uplink = ESX VDS Uplink1.*
  	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.4.3.step1.jpg">
	</p>   

  - **For each ESXi, configure its new "VDS - NSX-T"**  
  Click "Configure NSX".  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.4.3.step2a.jpg">
	</p>  
	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.4.3.step2b.jpg">
	</p>  
  - **For each ESXi, validate "VDS - NSX-T" creation.**  

	<p align="center">
	  <img width=75% height=75% src="/docs/assets/Graphics/2.4.3.step3.jpg">
	</p>  
</details>

</details>

---

### 5. Deployment of Edge Node


<details>
<summary>"Click to expand"</summary>

*Note: If you limit your Evaluation at [Security only (no Logical Network)](/docs/3.1-Security-Only.md) and not [Logical Network + Security](/docs/3.2-LogicalNetwork-Security.md) nor [Operation Tools](/docs/3.3-Operation-Tools.md), you don't need to deploy Edge Nodes.*

#### 5.1. Creation of VDS Port Group "All VLAN"

<details>
<summary>"Click to expand"</summary>

- **Create a Port Group "All VLAN" (= VLAN Tag 0-4096) on VDS.**  
From vCenter, under "Networking", select the VDS-NSX, and right-click to "New Distributed Port Group...".
*For this lab, see the top of page for this Port Group on VDS.*  
  	<p align="center">
	  <img width=40% height=40% src="/docs/assets/Graphics/2.5.1.step1.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.5.1.step2.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.5.1.step3.jpg">
	</p>  
  	<p align="center">
	  <img width=70% height=70% src="/docs/assets/Graphics/2.5.1.step4.jpg">
	</p>  

</details>

#### 5.2. Installation of NSX Edge Node

<details>
<summary>"Click to expand"</summary>

- **Deploy 1 Edge Node on ESXi.**  
Under "System - Configuration - Fabric - Nodes - Edge Transport Nodes", click "Add Edge VM".  
*Select Form Factor Medium (useful if you want to test later Load-Balancing),  
enable SSH for admin and root if you want to try later deeper troubleshooting,  
Management and Switch (TEP) IP addresses on the top of the page), and  
Transport Zones = "nsx-overlay-transportzone" (default TZ for Overlay traffic) and "nsx-vlan-transportzone" (default TZ for VLAN traffic).*
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.5.2.step1.jpg">
	</p>  
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.5.2.step2.jpg">
	</p>  
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.5.2.step3.jpg">
	</p>  
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.5.2.step4.jpg">
	</p>  
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.5.2.step5.jpg">
	</p>  
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.5.2.step6.jpg">
	</p>  

- **Validate Edge Node deployment.**  
Under "System - Configuration - Fabric - Nodes - Edge Transport Nodes", click "Refresh" (bottom UI)  
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.5.2.step7.jpg">
	</p>  

</details>

#### 5.3. Creation of Edge Cluster

<details>
<summary>"Click to expand"</summary>

- **Create 1 Edge Cluster with EdgeNode1 member.**  
Under "System - Configuration - Fabric - Nodes - Edge Clusters", click "Add".  
*Select EdgeNode1 as member of that Edge Cluster.*
	<p align="center">
	  <img width=50% height=50% src="/docs/assets/Graphics/2.5.3.step1.jpg">
	</p>  

- **Validate Edge Cluster creation.**  
Under "System - Configuration - Fabric - Nodes - Edge Clusters", click "Refresh".  
	<p align="center">
	  <img width=85% height=85% src="/docs/assets/Graphics/2.5.3.step2.jpg">
	</p>  


</details>

</details>

---

[***Next Step: 3. NSX Evaluation***](/docs/3-NSX-Evaluation.md)

