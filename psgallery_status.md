
PowerShell Gallery Status
=========================
### September 9th 2025, Unable to Install NuGet provider, cert expired error
When `Install-PackageProvider` from [OneGet](https://github.com/OneGet/oneget/issues/553) installs NuGet provider, users were seeing that the `Certificate has expired for https://onegetcdn.azureedge.net/` . The `.swidtag` file that OneGet needs `https://cdn.oneget.org/providers/nuget-2.8.5.208.package.swidtag` was pointing to the old CDN url that we moved off of when migrating CDNs. We purged the CDN and the link is now updated to the new one. We are investigating this further on our end, but believe the issue to be resolved for users. Please open an issue if you see this still occurring for you.

__Status: Mitigated__

### April 25th 2025, Slowness with downloads
We are noticing slowness for downloading packages from PSGallery and are working to resolve this.

__Status: This issue is being mitigated, if you are still experiencing this issue please let us know.__

### March 14th 2025, Incorrect display logins- UPDATE
Logins are working, but now only showing incorrect information (email address, specifically) for a small subset of users. To check if this affects you: log in to the PSGallery site with your usual credential, select your username in the top right corner and check if the email address displays as 'psgadmin@microsoft.com'. If so, on the same 'View Profile' page, click the pencil icon by your username, click and expand the 'Email Address' dropdown and input your desired email address, hit 'Save'. Please email us at 'psgadmin@microsoft.com' and we will remedy then it.
### March 14th 2025, Incorrect display logins
Logins are working, but showing in correct information.  The team is actively working on this issue. 
If you need to reach the PowerShellGallery team please directly email the team at psgadmin at microsoft.com. 

__Status: Ongoing__

### February 12th 2025, Email system is down
The PowerShellGallery team is investigating this issue and working on a solution.
If you need to reach the PowerShellGallery team please directly email the team at psgadmin at microsoft.com. 

__Status: Ongoing__

### January 28th 2025, Routine Maintenance

The PowerShellGallery team will be conducting routine maintenance on Tuesday Jan 28 from 11am-1pm PST. We expect this change to not affect users, but if you experience issues or slowness downloading, please let us know.

__Status: Resolved__

### January 13th 2025, CDN Migration off Edgio.

As part of a [migration off Edgio CDN](https://learn.microsoft.com/en-us/azure/cdn/edgio-retirement-faq), PowerShellGallery is updating its content delivery URLs. We expect this change to not affect users, but if you experience issues or slowness downloading, please let us know.

__Status: Resolved__

### August 16th 2024, Logins to the PowerShell Gallery are currently failing.

User logins to the PowerShell Gallery are currently failing, returning an Internal Server Error.  We are currently working on the issue and will resolve as quickly as possible.

__Status: Resolved__

### July 11th, 2024 Individual package statistics will be temporarily unavailable.

Individual package statistics will be temporarily unavailable while we are making infrastructure changes.  There will be no loss of information, however statistics numbers will temporarily not update.

__Status: Resolved__

### May 20th, 2024 The PowerShell Gallery is experiencing slowness.

The team is currently investigating and working on mitigating the issue as quickly as possible.

Status: Resolved


### May 13th, 2024  The [PowerShell Gallery](https://powershellgallery.com) is having issues with statistics.
__Status: Resolved__ 

__Summary of Impact__: Package download statistics were not getting updated on PowerShellGallery.com. Issue was resolved around 12:00:00 PST

### April 4, 2024 The [PowerShell Gallery](https://powershellgallery.com) is experiencing intermittent failures.
__Status: Resolved__

__Summary of Impact__: PowerShellGallery.com experienced an outage.  Users were be unable to access the gallery or download packages.  

__Root Cause__: Route cause was due to a SQL outage impacting PSGallery access to its database. Request failures began roughly 00:53 UTC on April 4, and resolved around 04:07 UTC. 

### March 4, 2024 The [PowerShell Gallery](https://powershellgallery.com) is experiencing an issue with account login.
The team is currently investigating and working on mitigating the issue as quickly as possible.
In the meantime users may not be able to log into the PSGallery, if you need to manage your package 
please contact support.

### January 5th, 2024 Aggregate statistics for PowerShell modules is not getting updated.
The team is currently investigating and working on mitigating the issue as quickly as possible.

### June 14th, 2022  The [PowerShell Gallery](https://powershellgallery.com) is down.
The team is currently investigating and working on mitigating the issue as quickly as possible.

__Status: Resolved__

### June 14th, 2022  The [PowerShell Gallery](https://powershellgallery.com) is having issues with "sign in".
The team is currently determining the root cause of this issue and is working to solve as quickly as possible. 

__Status: Resolved__

### May 2nd, 2022 16:41 UTC The [PowerShell Gallery](https://powershellgallery.com) is having issues with latency.
For the past week there have been reports of delays and extreme slowness with the PSGallery.  We're putting all our efforts into addressing this and more seriously looking into better ways to optimize our service. 

__Status: Mitigated__

### September 22nd, 2021
From Monday, September 27th to Thursday, September 30th a migration will occur to a new (ARM based) cloud service. We do not anticipate that this will interrupt traffic or interfer with Gallery access, but would like to notify users beforehand in case of unanticipated side effects.

If there are any availability issues during this time frame, please open an issue in the Gallery GitHub, or reach out to cgadmin@microsoft.com.

We'll be monitoring both closely to keep an eye on any erring behavior. 


### August 17th, 2021 20:45 UTC The [PowerShell Gallery](https://powershellgallery.com) is having issues with latency.
There is currently very low availability, with timeout errors when attempting to access the PSGallery.

__Status: Resolved__

### August 17th, 2021 20:00 UTC The [PowerShell Gallery](https://powershellgallery.com) is having issues allowing users to log in to accounts.
Users are currently unable to log in due to a an error with the Azure active directory app registration.  This issue is currently being investigated and new registrations are being created.

__Status: Resolved__

### July 6th, 2021 20:58 UTC The [PowerShell Gallery](https://powershellgallery.com) is experiencing latency due to lower availibility with CDN.

__Status: Resolved__

__Summary of Impact__: Users may experience latency when interacting with the Gallery, particularly when installing modules or scripts.

__Root Cause__: Since about 08:30 UTC the PowerShellGallery has experienced intermitten latency due to drops in availability with our CDN.  We believed this issue to be resolved at 16:03 UTC, but since 20:00 UTC availability has staggered between 20-80% availability.

Verizon supports our CDN and we have reached out to them to get support with the sudden drops.  We will continue to update our status as we figure out the root cause of this issue.    

### 06/03/2021 02:28 UTC The [PowerShell Gallery](https://powershellgallery.com) was unavailable via HTTPS.

__Status: Resolved__

__Summary of Impact__: Users were unable to access the gallery or download packages using HTTPS.  

__Root Cause__: The SSL certificate expired after the 3 months and the renewed certificate thumbprint was not updated after renewal. The renewal for these certificates was set to 80% of the lifespan of the certificate. Because the validity period is now only 3 months, it was renewed only about 8 days before the old cert became invalid. Thumbprint values have a Key Vault secret reference in the repository and this value gets retrieved and updated in the cloud service configuration file whenever a new cloud service is deployed. We have now changed the validity of the certificate to expire every one year, but will be renewed every three months. This gives us more time to update the configuration on the cloud service and will reduce the chances of any downtime. We are still working on automating the process to avoid any re-deployment.

### 03/22/2020 02:30 UTC The [PowerShell Gallery](https://powershellgallery.com) was unable via HTTPS.

__Status: Resolved__

__Summary of Impact__: Users were unable to access the gallery or download packages using HTTPS.  

__Root Cause__: In the last few months we addressed some internal compliance mandates to autorotate our certificates every 3 months. The renewal for these certs was set to 80% of the lifespan of the cert. Because our certificates were valid for a year this meant we had nealry 3 months to do a deployment in order to update the thumbprint to reference the new certificate (a timeframe in which our deployment cadence fell within). Because the validity period is now only 3 months, it was renewed only about 8 days before the old cert became invalid.  Thumbprint values have a Key Vault secret reference in the repository and this value gets retrieved and updated in the cloud service configuration file whenever a new cloud service is deployed. We are in the process of automating this process so that a deployment is not necessary to update a cert's thumbprint and thumbprints are updated upon cert renewal.




### 10/30/2020 18:15 UTC The [PowerShell Gallery](https://powershellgallery.com) is currently:  __Experiencing a continued outage

__Status: Resolved__

__Summary of Impact__: PowerShellGallery.com is experiencing an outage.  Users will be unable to access the gallery or download packages.  

__Root Cause__: Work was happening to migrate data lost from the last outage to get the statistics up-to-date.  However, an update to the database caused extremely high CPU/DTU utilization which tied up cloud service resources.  In an effort to mitigate this issue the production database was restored to a point in time where the database was in a stable state, however this restore caused an error in the configuration of the SQL cluster that resulted in the gallery front end not able to authenticate with the SQL backend.  Unfortunately, it took awhile to figure this out. Once that was identified, the SQL configuration was fixed and validated that basic operations are working again.  This means for now the statistics are not complete and we'll look at fixing that later after reviewing how this mistake occurred.  We are actively monitoring the gallery to ensure it maintains proper operation across all regions.


### 10/15/2020 - PowerShellGallery.com may temporarily experience latency and/or low availability 

Database updates will be made on Monday, October 19th at 9am and will last 10 minutes.  The update will lock specific tables in the database and may potentially impact search requests made to the gallery.  This should not impact package downloads. 

### 10/7/2020 - PowerShellGallery.com is experiencing low availability that may result in an inability to install package or access data on the website.

__Status: Resolved__

__Summary of Impact__: PowerShellGallery.com is experiencing lags and low availability.  Further updates will be made pending mitigation and resolution.  

__Root Cause__: Under investigation

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

