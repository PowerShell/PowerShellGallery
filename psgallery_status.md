
PowerShell Gallery Status
=========================
### The [PowerShell Gallery](https://powershellgallery.com) is currently:  __Working Normally__

### 6/11/2019 - PowerShellGallery.com is not responding

__Status: Resolved__

__Summary of Impact__: PowerShellGallery.com was unavailable between 8:15 AM and 11:15 AM Pacific Time. 

__Root Cause__: This occurred because of a routine configuration update the previous day: we updated a password used for sending email. The new password contained a character which was not valid as part of a URL, but the script used to perform the update did not correctly escape the character. This meant that each service instance as it restarted would read the new configuration and fail to load. This would have been caught in the test gallery, but the script also silently failed to restart the service instances, so nothing went wrong immediately and the configuration change was applied to the production gallery as well. As each service instance restarted afterwards, it entered a failed state. At the start of the incident, the last instances restarted and the service became unavailable.

__Resolution__: Changes have been made to the script and process used to roll out configuration changes to prevent this problem from recurring, and the service itself has also been made more robust against this kind of issue. 

### 10/24/2018 - Some downloads failing with 'End of Central Directory Record Could not be found'

__Status: Resolved__

__Summary of Impact__: Users in some regions reported issues downloading some packages. The downloads reported an error similar to: "Install-Package : Package 'AzureRM.profile' failed to be installed because: End of Central Directory record could not be found.".

This was due to an error in CDN configuration which lead to an invalid file being cached and served by some CDN regions. The issue is now believed resolved, please contact cgadmin@microsoft.com if you still see this problem.



### 9/13/2018 - Link to Facebook not working

__Status: Resolved__

__Summary of Impact__: The link from the package details pages to Facebook is not currently working. Root cause is being investigated. As a temporary workaround, users need to manually create entries in Facebook that link to their PowerShell Gallery items.

__Root Cause__: Related to update to newer gallery version

__Resolution__: Due to historical low usage, all the social media buttons (FaceBook, Twitter and LinkedIn) have been removed from the site.

__Next Steps__: 

### 9/13/2018 - Azure Automation integration was not working

__Status: Resolved__

__Summary of Impact__: The interaction between Azure Automation and PowerShell Gallery was broken temporarily. The links to the PowerShell Gallery from inside Azure Automation were not functioning. 

__Root Cause__: A configuration change was applied to Azure Automation that corrected the issue.

__Resolution__: Changes to data structures in the new PowerShell Gallery resulted in the Automation Gallery not being able to interpret the data. 

__Next Steps__: A configuration change has been applied, the issue is resolved to the best of our knowledge. 


## History of previous issues

### 10/10/2017 - PowerShell Gallery unavailable for 2 hours 10/10/17

__Status: RESOLVED__

__Summary of Impact__: The PowerShell Gallery experienced a period of very high latency, resulting in intermittent connection issues, beginning approximately 5pm (PDT) 10/10/17. While resolving the issue, the site was taken offline for 2 hours starting approximately 10pm (PDT). The site was restored shortly before midnight 10/10/2017. 
 
__Root Cause__: 

__Resolution__: The web services had to be taken offline and restored in order to address the primary issue. 

__Next Steps__: 

### 06/01/2017 - Deploy to Azure Automation Currently Unavailable

__Status: RESOLVED__

__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.  Importing items from the PowerShell Gallery from inside Azure Automation is still available.  
 
__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation. Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.

__Resolution__: Engineers are working to resolve issue.  The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation. 

__Next Steps__: Engineers will release the fix shortly.  In the meantime, please use the recommended workaround. 


### 04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts

__Status: RESOLVED__

__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts. 
 
__Root Cause__: During an update to interact more securely with AAD, a setting change was missed. 
The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.

__Resolution__: Engineers identified the missing setting and corrected the problem. 

__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.

### 03/27/2017 - RESOLVED: Unable to see individual module and script pages

__Status: RESOLVED__

__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken. This was being reported across all the regions. This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.

__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.  

__Resolution__: Engineers fixed the problem by disabling the Facebook count information.

__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.

### 12/15/2016 - Unable to send emails via PowerShellGallery website

__Status: RESOLVED__

__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.  
__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.  
__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.  
__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again. We apologize for the inconvenience.  



### 8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com

__Status: RESOLVED__

__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.  
__Root Cause__: Engineers identified the cause as a configuration change of the email account.  
__Resolution__: Engineers worked to resolve the configuration issue.  
__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again. Thank you for your patience.



### 7/13/2016 - Download Items Failed

__Status: RESOLVED__

__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery. The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:

```powershell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.  
__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.  
__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.


### 5/19/2016 - Download Items Failed

__Status: RESOLVED__

__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery. The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.  
__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.  
__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.

