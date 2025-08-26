# Azure ARM Parameters Project

This project demonstrates deploying an **Azure Storage Account** with an **Azure Resource Manager (ARM) template** that uses parameters, validation, and outputs.  
It was completed as part of my AZ-104 practice labs.

---

## What I Learned
- How to create parameters in an ARM template (`storageName`, `storageSKU`).
- How to enforce validation with `allowedValues`.
- How to deploy ARM templates using **PowerShell**.
- How to test valid and invalid parameter values.
- How to add outputs to return useful deployment information (storage account endpoints).
- How to verify deployments and outputs in the **Azure Portal**.

---

## Steps Completed

### Step 1 – Initial Template  
Created the basic ARM template structure.  
![Step 1](screenshots/01-stepone.png)

### Step 2 – Added Parameters  
Added the `storageName` parameter.  
![Step 2](screenshots/02-steptwo.png)

### Step 3 – Parameterized Deployment  
Deployed with the `storageName` parameter.  
![Step 3](screenshots/03-stepthree.png)

### Step 4 – Verified in Portal  
Deployment succeeded and appeared in the Resource Group.  
![Step 4](screenshots/04-stepfour.png)

### Step 5 – Added storageSKU Parameter  
Added `storageSKU` with allowed values and redeployed.  
![Step 5](screenshots/05-stepfive.png)

### Step 6 – Deployment with Valid SKU  
Deployed successfully using `Standard_GRS`.  
![Step 6](screenshots/06-stepsix.png)

### Step 7 – Deployment with Invalid SKU  
Tested with `Basic` and deployment failed (as expected).  
![Step 7](screenshots/07-stepseven.png)

### Step 8 – Added Outputs  
Modified template to return storage account endpoints.  
![Step 8](screenshots/08-stepeight.png)

### Step 9 – Verified Outputs in PowerShell  
Outputs appeared in the terminal as JSON with blob, dfs, file, queue, table, and web endpoints.  
![Step 9](screenshots/09-stepnine.png)

### Step 10 – Verified Outputs in Azure Portal  
Checked the Outputs tab in the Portal for the latest deployment.  
![Step 10](screenshots/10-stepten.png)

---

## Project Files
- `README.md` – This file (project overview).  
- `NOTES.md` – Commands used to deploy the template.  
- `screenshots/` – Screenshots showing each step of the process.  

---

## Summary
This project shows how ARM templates can:  
- Accept parameters  
- Validate inputs  
- Return outputs  

It demonstrates real-world Infrastructure as Code (IaC) practices with Azure, making deployments reusable and reliable.

