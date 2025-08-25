# Azure ARM Template Deployment – Storage Account

This project demonstrates how to create and deploy an Azure Resource Manager (ARM) template using **Visual Studio Code** and **Azure PowerShell**.  
The deployment provisions a **Resource Group** and a **Storage Account** in Azure.

---

## 📸 Screenshots Walkthrough

### 1. Blank ARM Template
Starting point: an empty `azuredeploy.json` ARM template in VS Code.  
![Blank ARM Template](01-Blank-ARM-template.png)

---

### 2. Connect to Azure
Logged into Azure using PowerShell (`Connect-AzAccount`).  
![Terminal After Login](02-terminal-after-log-in.png)

---

### 3. View Subscription
Verified available subscriptions with `Get-AzSubscription`.  
![Get Subscription](03-Get-AzSubscription.png)

---

### 4. Create Resource Group
Created a new resource group using `New-AzResourceGroup`.  
![Resource Group Created](04-resource-group-name-id-location.png)

---

### 5. Resource Group Provisioned
Confirmed the new resource group provisioned successfully.  
![Provisioning Succeeded](06-provisioning-succeeded.png)

---

### 6. Azure Portal Verification
Checked the deployment in the Azure Portal – resource group visible.  
![Azure Portal Deployment](07-azure-portal-deployment.png)

---

### 7. Edit ARM Template
Added a Storage Account resource definition to the ARM template.  
![Edit Template in VS Code](08-edit-vs-code.png)

---

### 8. Update SKU
Modified SKU from **Premium_LRS** to **Standard_LRS** to stay within free tier.  
![Update SKU](09-vs-code.png)

---

### 9. Deploy Template Again
Redeployed the updated template, resulting in **two deployments** (blank + storage).  
![Both Deployments](10-both-deployments.png)

---

### 10. Deployment Success – Storage
Verified the second deployment (`addstorage`) completed successfully.  
![Add Storage Deployment](11-add-storage-deployment.png)

---

### 11. Storage Account Resource
Confirmed the storage account resource was created inside the resource group.  
![Storage Account Resource](12-storage-resource.png)

---

## 🛠️ Tools & Technologies Used
- **Azure Resource Manager (ARM) Templates**
- **Visual Studio Code**
- **Azure PowerShell**
- **Azure Portal**

---

## 🏆 Outcome
Successfully created and deployed an ARM template that provisions:
- A **Resource Group** in `East US`
- A **Storage Account** with `Standard_LRS` configuration

This project demonstrates the full workflow of writing, deploying, and validating an ARM template in Azure.

---

## ⚠️ Cleanup (Optional)
To avoid any charges, delete the resource group when done:

```powershell
Remove-AzResourceGroup -Name MyARMResourceGroup -Force

