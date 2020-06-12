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
    $ az deployment group create --resource-group <resource-group-name> --template-uri https://raw.githubusercontent.com/prash2611/OneAgentTemplates/master/deployOneAgent.json --parameters vmName=<vm-name>
    ```
3. Installation  and configuration of OneAgent on a VM created during deployment using exiting LA Workspace.
    ```shell
    $ az deployment group create --resource-group <resource-group-name> --template-uri https://raw.githubusercontent.com/prash2611/OneAgentTemplates/master/deployOneAgent.json --parameters createNewVM=true vmName=<vm-name> vmImageName=<Ubuntu:18.04-LTS:latest> vmAdminUsername=<vm-admin-username> vmAdminPublicKey=<vm-admin-ssh-public-key> laWorkspaceName=<la-workspace-name>
    ```
4. Installation  and configuration of OneAgent on a VM created during deployment using a LA Workspace created during deployment.
    ```shell
    $ az deployment group create --resource-group <resource-group-name> --template-uri https://raw.githubusercontent.com/prash2611/OneAgentTemplates/master/deployOneAgent.json --parameters createNewVM=true vmName=<vm-name> vmImageName=<Ubuntu:18.04-LTS:latest> vmAdminUsername=<vm-admin-username> vmAdminPublicKey=<vm-admin-ssh-public-key>
    ```

## Private Preview Considerations
OneAgent is currently being private previewed. During this time there are some special considerations:
1. One Agent is only available in "East US" and "East US 2 EUAP" regions, so the VM has to be created in one these regions.
2. Subscription has to be whitelisted to use OneAgent. Please contact Azure Monitoring Config Service (AMCS) Team <amcsdev@microsoft.com> to request subscription whitelisting. Whitelisted subscription can be found [here](https://microsoft.sharepoint.com/teams/AutoupdateAzSecPack/_layouts/OneNote.aspx?id=%2Fteams%2FAutoupdateAzSecPack%2FShared%20Documents%2FGeneral%2FAutoUpdate-AzSecPack-StickyNotes&wd=target%28AzSecPack%20Extensions%20and%20OneAgent.one%7C88CD468F-A851-46E4-8B29-2CAAB57C687B%2FSubscription%20whitelist%20request%20for%20AMCS%7C38D9A9DF-ED1A-496F-9695-6F9D5D624774%2F%29).

## Syntax
### Using AZ CLI
```shell
$ az deployment group create --resource-group <resource-group-name> --template-uri https://raw.githubusercontent.com/prash2611/OneAgentTemplates/master/deployOneAgent.json --parameters vmName=<vm-name> [vmLocation=<vm-location>] [createNewVM=<true|false>] [vmImageName=<Ubuntu:18.04-LTS:latest>] [vmAdminUsername=<vm-admin-username>] [vmAdminPublicKey=<vm-admin-ssh-public-key>] [laWorkspaceName=<la-workspace-name>] [laWorkspaceLocation=<la-workspace-location>]
```

### Using Powershell
```powershell
PS> New-AzResourceGroupDeployment -ResourceGroupName <resource-group-name> -TemplateUri https://raw.githubusercontent.com/prash2611/OneAgentTemplates/master/deployOneAgent.json -vmName <vm-name> [-vmLocation <vm-location>] [-createNewVM <true|false>]  [-vmImageName <Ubuntu:18.04-LTS:latest>] [-vmAdminUsername <vm-admin-username>] [-vmAdminPublicKey <vm-admin-ssh-public-key>] [-laWorkspaceName <la-workspace-name>] [-laWorkspaceLocation <la-workspace-location>]
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
            "_comment": "Following are all optional parameters.",
            "vmLocation": {
                "value": "<vm-location>"
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
            "laWorkspaceName": {
                "value": "<la-workspace-name>"
            },
            "laWorkspaceLocation": {
                "value": "<la-workspace-location>"
            }
        }
    }
}
```

### Using Azure portal
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fprash2611%2FOneAgentTemplates%2Fmaster%2FdeployOneAgent.json)
