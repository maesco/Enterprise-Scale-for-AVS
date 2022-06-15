# Configure Monitoring

It is crucial to monitor the resource utilization in order to take timely action. This tutorial walks through setting up Azure Monitor alerts for Azure VMware Solution Private Cloud. Action owners will receive email notifications if utilization metrics exceeds set threshold.

This scenario also includes service health alerts to ensure you don't miss any updates or events that may impact the target Private Cloud.

## Prerequisites

* AVS Private Cloud up and running.

* A list of email address(es) who will receive Alerts from Azure VMware Solution Private Cloud.

## Deployment Steps

* Update the parameter values in appropriate parameter file.
   
* Run one of the following scripts.

### Parameter Values

| Parameter | Description |
--- | --- |
| Subscription | All resources in an Azure subscription are billed together. |
| Resource Group | A resource group is a collection of resources that share the same lifecycle, permissions, and policies.|
| Region | A resource group is a collection of resources that share the same lifecycle, permissions, and policies. |
| Action Group Name | Name of the action group to be created |
| Alert Prefix | Prefix to use for alert creation |
| Action Group Email | Email addresses to be added to the action group. Use the format ["name1@domain.com","name2@domain.com"]. |
| Private Cloud Resource Id | The existing Private Cloud full resource id. Use the format /subscriptions/<subscription_ID>/resourceGroups/<ResourceGroup_Name>/providers/Microsoft.AVS/privateClouds/<AVS_PrivateCloud_Name>. |

### Bicep

```azurecli-interactive
cd Bicep

az deployment group create -g AVS-Step-By-Step-RG -n AVS-Monitoring-Deployment -c -f "AVSMonitor.bicep" -p "@AVSMonitor.parameters.json"
```

### ARM

```powershell
cd ARM

az deployment group create -g AVS-Step-By-Step-RG -n AVS-Monitoring-Deployment -c -f "AVSMonitor.deploy.json" -p "@AVSMonitor.parameters.json"
```

## Post-deployment Steps

* Navigate to Azure Monitor service in Azure Portal. Click "Alerts" tab and navigate to "Manage alert rules". Newly created alert - *AVSAlert* - should be listed with status as "Enabled".

## Next Steps

[Configure SRM](../../Addons/SRM/readme.md)
