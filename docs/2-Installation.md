
## Installation of NSX

### Validation of pre-requirements

| Compute           | Number        | Version   | Download |
|:------------------|:-------------:|:---------:|:--------:|
| vCenter           | 1             | 7.0       | link     |
| Cluster           | 1+            | n/a       | n/a      |
| ESXi per Cluster  | 2+            | 7.0       | link     |
| NIC per ESXi      | 2+            | n/a       | n/a      |

| Storage        |                                    |
|:---------------|:----------------------------------:|
| Size           | xxx GB                             |
| Shared storage | recommended for live vMotion tests |


<p align="center">
  <img width=20% height=20% src="/docs/assets/Graphics/2.1.Pre-Req Compute.jpg">
</p>


xxx Add picture xxx
- vCenter 7.0 with 1 Cluster + 2 ESXi 7.0
- ESXi with 2 pNICs (1 used for Mgr + 1 unused)
- Storage x GB available


