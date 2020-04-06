
## 1. Requirements

Here are the requirements for NSX-T Evaluation.

#### Compute & Storage

<details>
<summary>"Click to expand"</summary>

<p align="center">
  <img width=75% height=75% src="/docs/assets/Graphics/1.1.Pre-Req Compute.jpg">
</p>

| Compute          | Number | Version |                                                      Download                                                       |
|:-----------------|:------:|:-------:|:-------------------------------------------------------------------------------------------------------------------:|
| vCenter          |   1    |   7.0   |  [download link](https://my.vmware.com/en/web/vmware/info/slug/datacenter_cloud_infrastructure/vmware_vsphere/7_0)  |
| vCenter-Cluster  |   1+   |   n/a   |                                                         n/a                                                         |
| ESXi per Cluster |   2+   |   7.0   | [download link xxx](https://my.vmware.com/en/web/vmware/info/slug/networking_security/vmware_nsx_t_data_center/2_x) |
| CPU per ESXi     |   8+   |   n/a   |                                                         n/a                                                         |
| RAM per ESXi     | 48GB+  |   n/a   |                                                         n/a                                                         |
| NIC per ESXi     |   2+   |   n/a   |                                                         n/a                                                         |

| Storage | Shared storage - Recommended for live vMotion tests |
|:--------|:---------------------------------------------------:|
| Size    |                       500 GB                        |

</details>

---

#### Networking

<details>
<summary>"Click to expand"</summary>

<p align="center">
  <img width=75% height=75% src="/docs/assets/Graphics/1.2.Pre-Req Networking.jpg">
</p>

| VLAN       | Number  | Description                                                                                  |
|:-----------|:-------:|:---------------------------------------------------------------------------------------------|
| Management | VLAN 11 | VLAN where Management is running (vCenter / ESXi-Mgt / future NSX-Mgr / future EdgeNode-Mgt) |
| Overlay    | VLAN 12 | VLAN where future NSX Logical Switches Overlay will run in                                   |

| Physical Router |                                                                                                                      |
|:----------------|:---------------------------------------------------------------------------------------------------------------------|
| Interface       | 1 interface on each of those VLAN                                                                                    |
|                 | *Note: Since in this lab Overlay will run only in VLAN 12, there is no need to enable large MTU on router interface* |

*Note:  
In the section "3.1. Security only (no Logical Network)", 1 new VLAN + interface will be created on Physical Router.  
In the section "3.2. Logical Network + Security", 1 new VLAN + interface will be created on Physical Router.*  


</details>


---

[***Next Step: 2. Installation of NSX***](/docs/2-Installation.md)
