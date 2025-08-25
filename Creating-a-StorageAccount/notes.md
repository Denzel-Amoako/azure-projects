# 📝 Notes – Azure ARM Template Deployment (Storage Account)

This file contains my raw notes, commands, and terminal outputs during the project.  
It complements the main [README.md](./README.md).

---

## 1️⃣ Blank ARM Template
Created an empty ARM template in VS Code.

**File: `azuredeploy.json`**
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {},
  "functions": [],
  "variables": {},
  "resources": [],
  "outputs": {}
}

---

## 2️⃣ Connect to Azure
Command:
Connect-AzAccount  
✅ Logged into Azure successfully.

---

## 3️⃣ View Subscriptions
Command:
Get-AzSubscription  

**Sample Output (simplified):**
- SubscriptionName : Azure subscription 1  
- SubscriptionId   : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX  
- State            : Enabled  

---

## 4️⃣ Set Context
Command:
Set-AzContext -Subscription "Azure Subscription 1"

---

## 5️⃣ Create Resource Group
Command:
New-AzResourceGroup -Name MyARMResourceGroup -Location eastus  

**Output:**
- ResourceGroupName : MyARMResourceGroup  
- Location          : eastus  
- ProvisioningState : Succeeded  

---

## 6️⃣ Deploy Blank Template
$templateFile = "azuredeploy.json"  
$today = Get-Date -Format "MM-dd-yyyy"  
$deploymentName = "blanktemplate-" + $today  

New-AzResourceGroupDeployment -Name $deploymentName -ResourceGroupName MyARMResourceGroup -TemplateFile $templateFile  

**Output:**
- DeploymentName    : blanktemplate-08-25-2025  
- ResourceGroupName : MyARMResourceGroup  
- ProvisioningState : Succeeded  

---

## 7️⃣ Update Template – Add Storage Account
Updated `azuredeploy.json` with a storage account:

{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {},
  "functions": [],
  "variables": {},
  "resources": [
    {
      "name": "storageaccount12162001",
      "type": "Microsoft.Storage/storageAccounts",
      "apiVersion": "2023-05-01",
      "tags": {
        "displayName": "storageaccount1"
      },
      "location": "[resourceGroup().location]",
      "kind": "StorageV2",
      "sku": {
        "name": "Standard_LRS"
      }
    }
  ],
  "outputs": {}
}

---

## 8️⃣ Deploy Updated Template
$templateFile = "azuredeploy.json"  
$today = Get-Date -Format "MM-dd-yyyy"  
$deploymentName = "addstorage-" + $today  

New-AzResourceGroupDeployment -Name $deploymentName -ResourceGroupName MyARMResourceGroup -TemplateFile $templateFile  

**Output:**
- DeploymentName    : addstorage-08-25-2025  
- ResourceGroupName : MyARMResourceGroup  
- ProvisioningState : Succeeded  

---

## 9️⃣ Verify in Azure Portal
- Deployments Tab:  
  - blanktemplate-08-25-2025 ✅ Succeeded  
  - addstorage-08-25-2025 ✅ Succeeded  

- Resources Tab:  
  - storageaccount12162001 created in East US  
  - Replication: Locally-redundant storage (LRS)  
  - Performance: Standard  

---

## 🔟 Cleanup (Optional)
Remove-AzResourceGroup -Name MyARMResourceGroup -Force  

---

## ✅ Key Notes
- Used Standard_LRS (free tier safe).  
- Deployment mode = Incremental (does not overwrite existing resources).  
- Practiced JSON template editing and PowerShell deployment workflow.  
