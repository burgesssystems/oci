# OCI Automation Playbooks
## Introduction
This code reposity has sample Ansible playbooks for automating Oracle Cloud Infrastructure (OCI) resources.
## Catalogue
[set_bv_tier.yml](https://github.com/burgesssystems/oci/blob/main/set_bv_tier.yml) - Ansible playbook to modify the block volume performance VPU's for a given instance.
## Installation

Please follow the [Getting Started with Oracle Cloud Infrastructure and Ansible](https://docs.oracle.com/en-us/iaas/Content/API/SDKDocs/ansiblegetstarted.htm#Getting_Started_with_Oracle_Cloud_Infrastructure_and_Ansible) steps before running these playbooks.

## Authentication
The playbooks use API keys for authentication to OCI. Group, resource and tag policies are implemented to restrict playbook operations to resources in scope only.
## Configuration
### Block Volume Tags
The [set_bv_tier.yml](https://github.com/burgesssystems/oci/blob/main/set_bv_tier.yml) playbook requires specific tags configured on the block volumes to be managed.

**Tag Namespace**

- ResourceLabels
  - EnvironmentName
    - <<ENV_NAME1>>
    - <<ENV_NAME2>>
    - ..
  - Tier
    - Database
    - Application
    - NFS
- StoragePerformanceTierHigh
  - ApplicationTier
    - 0,10
  - DatabaseTier
    - 0,10,20
  - NFSTier
    - 10
- StoragePerformanceTierLow
  - ApplicationTier
    - 0,10
  - DatabaseTier
    - 0,10,20
  - NFSTier
    - 0

  Assign the ResourceLabels:EnvironmentName and ResourceLabels:Tier to all block volumes in scope.

  Assign the StoragePerformanceTierHigh:ApplicationTier and applicable setting to application server volumes.

  Assign the StoragePerformanceTierLow:ApplicationTier and applicable setting to application server volumes.

  Assign the StoragePerformanceTierHigh:DatabaseTier and applicable setting to database server volumes.

  Assign the StoragePerformanceTierLow:DatabaseTier and applicable setting to database server volumes.

  

