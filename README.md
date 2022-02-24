# windows_key_management_service
Install and configure Windows KMS

Requirements
------------

Windows clients with WinRM configured.

Module Windows are required.

```bash
ansible-galaxy collection install ansible.windows
ansible-galaxy collection install community.windows
```

Role Variables
--------------

In default, you can surcharge them.

```yaml
is_kms_host: false # Choose if your target is a KMS host
kms_port: 1688 # Default port for KMS
kms_hostname: '' # Define hostname of your KMS host
offline_installation: false # Select if you install KMS in a disconnected environment
kms_office_installation: false # Select if you need to activate office with your KMS host
kms_office_informations: # Information for Office Volume License Pack installation
  - edition: 'Office LTSC 2021'
    url_pack: 'https://download.microsoft.com/download/8/e/e/8eef6160-396a-4c26-830d-9e2a24c00309/Office2021VolumeLicensePack_x64.exe'
kms_host_licences: # Informations for KMS Host license
  - edition: 'Windows Server 2022 Datacenter'
    type: 'os'
    key: 'WX4NM-KYWYW-QJJR4-XV3QB-6VM33'
```
In vars, this GVLK are provided by Microsoft.

```yaml
kms_clients:
  - edition: 'Microsoft Windows Server 2022 Datacenter' 
    type: 'os'
    gvlk: 'WX4NM-KYWYW-QJJR4-XV3QB-6VM33'
```

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: windows
      roles:
        - role: windows_key_management_service
          

License
-------

MIT License

Sources
-------

https://docs.microsoft.com/en-us/windows-server/get-started/kms-client-activation-keys
https://docs.microsoft.com/fr-fr/DeployOffice/vlactivation/configure-a-kms-host-computer-for-office