---
title: "Authenticating with a service principal"
date: 2019-11-12T21:04:06Z
draft: false
---

It turns out that in Azure at least, not everything works first time. So for those times when you absolutely positively dont beloeve that your service principal is working, here is how to login with that resource.

```powershell
$azureAplicationId ="Azure AD Application Id"
$azureTenantId= "Your Tenant Id"
$azurePassword = ConvertTo-SecureString "strong password" -AsPlainText -Force
$psCred = New-Object System.Management.Automation.PSCredential($azureAplicationId , $azurePassword)
Add-AzureRmAccount -Credential $psCred -TenantId $azureTenantId  -ServicePrincipa
```