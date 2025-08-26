# Azure ARM Parameters Project – Notes

This file contains the exact PowerShell commands used during each step of the project.

## Step 1 – Initial Template
Created a blank ARM template. No commands for this step – just authored the `azuredeploy.json` file.

## Step 2 – Added Parameters
Added the `storageName` parameter to the template.

## Step 3 – Parameterized Deployment
Deployed the template using the `storageName` parameter.
$templateFile="azuredeploy.json"
$today=Get-Date -Format "MM-dd-yyyy"
$deploymentName="addnameparameter-" + $today
New-AzResourceGroupDeployment `
  -Name $deploymentName `
  -ResourceGroupName MyARMResourceGroup `
  -TemplateFile $templateFile `
  -storageName denzelstore082625

## Step 4 – Verified in Portal
Checked the deployment in the Azure Portal under Resource Group → Deployments.

## Step 5 – Added storageSKU Parameter
Added the `storageSKU` parameter with `allowedValues` to the template.

## Step 6 – Deployment with Valid SKU
Deployed successfully with a valid SKU (Standard_GRS).
$today=Get-Date -Format "MM-dd-yyyy"
$deploymentName="addSkuParameter-" + $today
New-AzResourceGroupDeployment `
  -Name $deploymentName `
  -ResourceGroupName MyARMResourceGroup `
  -TemplateFile azuredeploy.json `
  -storageName denzelstore082625 `
  -storageSKU Standard_GRS

## Step 7 – Deployment with Invalid SKU
Tried deploying with Basic (not in allowed values). Deployment failed as expected.
$today=Get-Date -Format "MM-dd-yyyy"
$deploymentName="addSkuParameter-" + $today
New-AzResourceGroupDeployment `
  -Name $deploymentName `
  -ResourceGroupName MyARMResourceGroup `
  -TemplateFile azuredeploy.json `
  -storageName denzelstore082625 `
  -storageSKU Basic

## Step 8 – Added Outputs
Modified template to add outputs for the storage account endpoints.

## Step 9 – Verified Outputs in PowerShell
Deployed the template again and viewed the outputs in the terminal.
$today=Get-Date -Format "MM-dd-yyyy"
$deploymentName="addOutputs-" + $today
New-AzResourceGroupDeployment `
  -Name $deploymentName `
  -ResourceGroupName MyARMResourceGroup `
  -TemplateFile azuredeploy.json `
  -storageName denzelstore082625 `
  -storageSKU Standard_LRS

## Step 10 – Verified Outputs in Azure Portal
Checked the Outputs tab of the deployment in the Azure Portal. The endpoints for blob, dfs, file, queue, table, and web were listed.

