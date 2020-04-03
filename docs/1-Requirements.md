
## 1. Requirements

Here are the requirements for NSX-T Evaluation

<details>
<summary>"Click to expand"</summary>

| Compute           | Number        | Version   | Download |
|:------------------|:-------------:|:---------:|:--------:|
| vCenter           | 1             | 7.0       | link     |
| Cluster           | 1+            | n/a       | n/a      |
| ESXi per Cluster  | 2+            | 7.0       | link     |
| NIC per ESXi      | 2+            | n/a       | n/a      |


| Storage        |                                    |
|:---------------|:-----------------------------------|
| Size           | xxx GB                             |
| Shared storage | recommended for live vMotion tests |


| Physical Network    |                                        |
|:-------------------|:---------------------------------------|
| VLAN               | Ability to create new VLAN             |
| Router             | Ability to create interfaces on router |


</details>


---

### Validation of Requirements

#### Compute & Storage

<details>
<summary>"Click to expand"</summary>

<p align="center">
  <img width=75% height=75% src="/docs/assets/Graphics/1.1.Pre-Req Compute.jpg">
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

</details>


#### Networking

<details>
<summary>"Click to expand"</summary>

<p align="center">
  <img width=75% height=75% src="/docs/assets/Graphics/1.2.Pre-Req Networking.jpg">
</p>

| VLAN       | Number      | Description                                         |
|:-----------|:-----------:|:----------------------------------------------------|
| Management | VLAN 11     | VLAN where Management is running (vCenter / ESXi-Mgt / future NSX-Mgr / future EdgeNode-Mgt) |
| Web        | VLAN 3104   | VLAN where Web VMs will run (for Security only test) |
| Overlay    | VLAN 12     | VLAN where future NSX Logical Switches Overlay will run in |
| External   | VLAN 3103   | VLAN where future NSX Logical Router will connect to provide "North/South" or "Logical/Physical" connectivity |


| Physical Router |                                                     |
|:----------------|:----------------------------------------------------|
| Interface       | 1 interface on each of those VLAN                   |
|                 | *Note: Since overlay will run only in VLAN30, there is no need to enable large MTU on router interface* |

</details>

---

[**Next Step: Installation of NSX**](/docs/2-Installation.md)
