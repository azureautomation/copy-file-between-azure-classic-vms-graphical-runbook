Copy File Between Azure Classic VMs Graphical Runbook
=====================================================

            

The runbook copies a file from one Azure Classic VM to other Azure Classic VM.


**Runbook parameters:**

-***AzureSubscriptionName <string>*** - name of the Azure subscription, the VMs belong to.

-***Azure_OrgId_CredentialAsset_Name <string>*** - name of the Automation Credential asset storing an OrgID credential with access to the Azure subscription (see [http://azure.microsoft.com/blog/2014/08/27/azure-automation-authenticating-to-azure-using-azure-active-directory/](http://azure.microsoft.com/blog/2014/08/27/azure-automation-authenticating-to-azure-using-azure-active-directory/) for
 details). Make sure you have the Automation Credential asset with such name created in the Automation account the runbook is being imported to.

-***Source_VM_Name <string>*** - name of the VM to copy the file from.

-***Source_VM_ServiceName <string>*** - service, the source VM is under. For Classic VMs the service name value is typically the same as the VM name.

-***Source_VM_CredentialAsset_Name <string>*** - name of the Automation Credential asset storing the login credential for the Source VM. Make sure you have the Automation Credential
 asset with such name created in the Automation account the runbook is being imported to.

-***Source_VM_Source_FilePath <string>*** - path to the file to be copied, for example: **C:\folder1\file1.txt**

-***Target_VM_Name <string>*** - name of the VM to copy the file to.

-***Target_VM_ServiceName <string>*** - service, the target VM is under. For Classic VMs the service name value is typically the same as the VM name.

-***Target_VM_CredentialAsset_Name <string>*** - name of the Automation Credential asset storing the login credential for the Target VM. Make sure you have the Automation Credential
 asset with such name created in the Automation account the runbook is being imported to.

-***Target_VM_Target_FilePath <string>*** - path to the file on the Target VM after copying, for example: **D:\folder2\file1.txt**. If the file does not exist - it will be created
 (all folders along the way will be automatically created), otherwise the file's content will be forcefully overwritten.

![Image](https://github.com/azureautomation/copy-file-between-azure-classic-vms-graphical-runbook/raw/master/Copy-FileBetweenAzureVMs.PNG)


**Notes:**


  *  Both VMs should be up and running, the runbook does not have a logic to start the VMs.

  *  Automation account needs to have 3 credential assets created:

  *  OrgID user login credential to Azure subscription 
  *  User login credential to Source VM 
  *  User logic credential to Target VM 

  *  File size should not be too big, because the copying process goes through the environment hosting the runbook execution, where limitations on the storage resources take place:


  *  File content is read from the Source VM to the runbook execution host environment

  *  Then the file bytes are being written to the Target VMs file system 

 

 

 


    
TechNet gallery is retiring! This script was migrated from TechNet script center to GitHub by Microsoft Azure Automation product group. All the Script Center fields like Rating, RatingCount and DownloadCount have been carried over to Github as-is for the migrated scripts only. Note : The Script Center fields will not be applicable for the new repositories created in Github & hence those fields will not show up for new Github repositories.
