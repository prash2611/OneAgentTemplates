# OneAgent Templates

## Overview
OneAgent templates aims to provide one click installation and configuration of all extensions and dependencies that are required to successfully onboard and use entire security monitoring that OneAgent provides.

These templates enables following scenarios:
1. Installation  and configuration of OneAgent on an existing VM using exiting LA Workspace.
    ```shell
    $ az deployment group create --resource-group <resource-group-name> --template-uri https://raw.githubusercontent.com/prash2611/OneAgentTemplates/master/deployOneAgent.json --parameters vmName=<vm-name> laWorkspaceName=<la-workspace-name>
    ```
2. Installation  and configuration of OneAgent on an existing VM using a LA Workspace created during deployment.
    ```shell
    $ az deployment group create --resource-group <resource-group-name> --template-uri https://raw.githubusercontent.com/prash2611/OneAgentTemplates/master/deployOneAgent.json --parameters vmName=<vm-name> createNewLAWorkspace=true laWorkspaceName=<la-workspace-name>
    ```
3. Installation  and configuration of OneAgent on a VM created during deployment using exiting LA Workspace.
    ```shell
    $ az deployment group create --resource-group <resource-group-name> --template-uri https://raw.githubusercontent.com/prash2611/OneAgentTemplates/master/deployOneAgent.json --parameters createNewVM=true vmName=<vm-name> vmImageName=<Ubuntu:18.04-LTS:latest> vmAdminUsername=<vm-admin-username> vmAdminPublicKey=<vm-admin-ssh-public-key> laWorkspaceName=<la-workspace-name>
    ```
4. Installation  and configuration of OneAgent on a VM created during deployment using a LA Workspace created during deployment.
    ```shell
    $ az deployment group create --resource-group <resource-group-name> --template-uri https://raw.githubusercontent.com/prash2611/OneAgentTemplates/master/deployOneAgent.json --parameters createNewVM=true vmName=<vm-name> vmImageName=<Ubuntu:18.04-LTS:latest> vmAdminUsername=<vm-admin-username> vmAdminPublicKey=<vm-admin-ssh-public-key> createNewLAWorkspace=true laWorkspaceName=<la-workspace-name>
    ```

## Syntax
### Using AZ CLI
```shell
$ az deployment group create --resource-group <resource-group-name> --template-uri https://raw.githubusercontent.com/prash2611/OneAgentTemplates/master/deployOneAgent.json --parameters vmName=<vm-name> laWorkspaceName=<la-workspace-name> [vmLocation=<vm-location>] [laWorkspaceLocation=<la-workspace-location>] [createNewVM=<true|false>] [vmImageName=<Ubuntu:18.04-LTS:latest>] [vmAdminUsername=<vm-admin-username>] [vmAdminPublicKey=<vm-admin-ssh-public-key>] [createNewLAWorkspace=<true|false>]
```

### Using Powershell
```powershell
PS> New-AzResourceGroupDeployment -ResourceGroupName <resource-group-name> -TemplateUri https://raw.githubusercontent.com/prash2611/OneAgentTemplates/master/deployOneAgent.json -vmName <vm-name> -laWorkspaceName <la-workspace-name> [-vmLocation <vm-location>] [-laWorkspaceLocation <la-workspace-location>] [-createNewVM <true|false>]  [-vmImageName <Ubuntu:18.04-LTS:latest>] [-vmAdminUsername <vm-admin-username>] [-vmAdminPublicKey <vm-admin-ssh-public-key>] [-createNewLAWorkspace true]
```

### Using ARM template

```json
{
    "name": "DeployOneAgent",
    "type": "Microsoft.Resources/deployments",
    "apiVersion": "2018-05-01",
    "properties": {
        "mode": "Incremental",
        "templateLink": {
            "uri": "https://raw.githubusercontent.com/prash2611/OneAgentTemplates/master/deployOneAgent.json"
        },
        "parameters": {
            "vmName": {
                "value": "<vm-name>"
            },
            "laWorkspaceName": {
                "value": "<la-workspace-name>"
            },
            
            "_comment": "Following are all optional parameters.",
            "vmLocation": {
                "value": "<vm-location>"
            },
            "laWorkspaceLocation": {
                "value": "<la-workspace-location>"
            },
            "createNewVM": {
                "value": "<true|false>"
            },
            "vmImageName": {
                "value": "<Ubuntu:18.04-LTS:latest>"
            },
            "vmAdminUsername": {
               "value": "<vm-admin-username>"
            },
            "vmAdminPublicKey": {
                "value": "<vm-admin-ssh-public-key>"
            },
            "createNewLAWorkspace": {
                "value": "<true|false>"
            }
        }
    }
}
```

### Using Azure portal
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fprash2611%2FOneAgentTemplates%2Fmaster%2FdeployOneAgent.json)
