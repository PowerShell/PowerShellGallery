
# Preview PowerShell Gallery Release Notes

## What has changed?
The PowerShell Gallery site is being updated to a new look, with some new features. Today, the changes are available via [https://www.Preview.PowerShellGallery.Com](https://www.Preview.PowerShellGallery.Com). 

**Please try out our new site and give us feedback!**

We started this work to improve the performance of acquiring items from the PowerShell Gallery, particularly outside the US. While we were making the change, we are taking the opportunity to add security features and update the look of the PowerShell Gallery to a more current design. 

Most of the new features come from the latest NuGet server code, as we are aligning more with them. Some of the features in this preview include:

* Improved download performance provided via CDN
* Enhanced security for publishers, including multiple publishing keys, and never displaying keys (see Managing API Keys, below)
* Account management support for changing email address or login account
* Direct download of items (as .Nupkg files)
* UI updated to be more responsive 

All items in this preview will also be available in the production PowerShellGallery site. The [Preview PowerShell Gallery](https://preview.powershellgallery.com) interacts with all the same items, and tracks all the same statistics, as [PowerShellGallery.com](https://powershellgallery.com)  

Once we have enough feedback and testing of these changes, the original UI will be retired and everyone will get the new experience. That change is expected this fall (2018).

## How to get started?

The preview site url is [https://www.Preview.PowerShellGallery.Com](https://Preview.PowerShellGallery.Com). 
Start by browsing to the site and checking out the new look.

To use this new site with PowerShellGet, you must register this as a PS Repository, then specify that repository with the PowerShellGet cmdlets, as shown in the example below:

```powershell
Register-PSRepository -Name PSGalleryPreview -SourceLocation https://www.Preview.PowerShellGallery.Com/api/v2 
Find-Module DSC* -Repository PSGalleryPreview
Install-Module DSCTestModule -Repository PSGalleryPreview -Verbose
```
Note that while both PSGallery and PSGalleryPreview repositories are registered, you will see errors when running Install-Module or Install-Script, because the same items will be returned by both repositories. Either specify the repository explicitly, as above, or see "Advanced users please try this" below.

Note that Register-PSRepository only needs to be done once for each user, and persists across PowerShell sessions. 

## What would we like you to try out?
Some of the newer features that we want people to try out are:

* Help us validate CDN by downloading large modules, or modules with many dependencies. Azure modules are a good place to start. Please use the "Contact us" link in the Gallery if you encounter an error during download that includes the reason "End of Central Directory record could not be found." 
* The new PowerShell Gallery Account management allows changing the email address, or the MSA account associated with a Gallery user. You should also check out notifications generated when your module is updated.
* Please try publishing (important instructions are below). If you have multiple modules, try using different API keys to publish them. 
* We want feedback for the default view on the new page for items - a module or a script. The new page collapses out much of the detail shown previously. Are we showing what is needed most?

## What is not right?

The following things are known to not work as expected. 
If you encounter something that is not listed here, please create an entry in our [issues list](https://github.com/PowerShell/PowerShellGallery/issues). 

The list is organized generally by the page where the issue will most likely be encountered.

* **Publishing to Preview requires a newer NuGet**:
Publishing to the Preview PowerShell Gallery requires a new NuGet.exe. An updated version (likely 1.6.6) of PowerShellGet is coming shortly that will include it. Until it is available, users must follow the instructions below to manually update NuGet.exe if they wish to publish to the PowerShell Gallery. 
* **I get failures trying to install the Azure modules from this site**:
The Preview PowerShell Gallery is seen and registered as a different location than PowerShellGallery.com. When you try to re-install a module from a new location, you will need to specify "-Force". 
As an example, the same versions of the Azure SDK team's modules are on both preview.powershellgallery.com and powershellgallery.com. If you try to install the same version of an item that you already have, install-module will skip it.
* **The commenting system is gone**:
The Preview PowerShell Gallery does not show the Comments section, or previous comments, that are visible at the bottom of each item detail page in the PowerShell Gallery. That section is provided by the LiveFyre service. At this time, we are unable to keep comments aligned between the Preview and public PowerShell Gallery sites. Rather than have someone provide feedback that is lost, we have disabled the feature for now. If you wish to provide feedback on an item, please go to [PowerShellGallery.com](https://powershellgallery.com), locate the same item, and provide your feedback there. 
* **I cannot change my sign-in account**:
The new sign-in experience does not give any chance to provide a login ID if the user is already logged in to a Microsoft or Azure Active Directory account. This is something we are working on with the NuGet team and expect to correct in the near future. Until that time this can be worked around by using an InPrivate (Edge/IE) or Incognito (Chrome) session. This will ensure that you receive a prompt for which account to use. 
* **Installing to Azure Automation is not yet working**: 
Three installation options are listed on the details page for any item. The Azure Automation option replaces the previous "Deploy to Azure Automation", but it is not currently functioning.
* Item statistics page: 
There are 2 options on the item statistics page that do not apply to the PowerShell Gallery, and will be removed: client name and client version. These are left over from our port of the NuGet code. 

## How to publish a module to the preview Gallery?

As mentioned above, the same content and accounts that exist at PowerShellGallery.com are also available via Preview.PowerShellGallery.com. However, publishing via the new location does have some differences.

You must register a new PS Repository to publish to the PowerShell Gallery, then add the respository flag to your publish command, as in:

```powershell
Register-PSRepository -Name PSGalleryPreview -SourceLocation https://www.Preview.PowerShellGallery.Com/api/v2 
Publish-Module -Path 'C:\Projects\PowerShell\SuperModule' -NuGetApiKey "NotIncludedHere" -Repository PSGalleryPreview
```

Users who have published previously can use the same APIKey they have used for PowerShellGallery.com.

You must upgrade your version of NuGet.exe to at least 4.1.0.  We will be releasing an updated version of PowerShellGet shortly that will force this update, but for now this must be done manually. You can upgrade by downloading NuGet.exe from https://www.nuget.org/downloads (latest version: https://dist.nuget.org/win-x86-commandline/latest/nuget.exe). You may use one of the two commands below, depending on whether you want the change for the current user or for all users:

```powershell
# Non-admin
Invoke-WebRequest -Uri https://aka.ms/psget-nugetexe -OutFile "$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\PowerShellGet\NuGet.exe"
```

```powershell
# Admin
Invoke-WebRequest -Uri https://aka.ms/psget-nugetexe -OutFile "$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet\NuGet.exe"
```

## Advanced users please try this...

Users who are willing should consider unregistering the default (PSGallery) repository, and using the preview as their primary or default PSRepository.  

It is not possible to change the registration for PSGallery to go to a different URL. Instead, what you must do is unregister PSGallery, and leaving only GalleryPreview registered, as in:

```powershell
Unregister-psrepository –Name PSGallery
Get-PSRepository
```

If the preview gallery is the only repository listed, it will be the default.  Once that is done, Find-, Install-, and Save-Module will work with Preview gallery without having to specify the Repository. Publishers will still need to specify –Repository, because Publish-Module only allows the PSGallery to be the default. 

To revert to using the production site, please use:
 
```powershell 
Unregister-PSRepository –Name PSGalleryPreview
Register-PSRepository –Default
```

Please note: The preview URL will go away when we transition the changes in preview to the production PowerShell Gallery, which will happen in the fall of 2018. This will break any automation that uses the preview URL as its target. We will, of course, be communicating that change via the preview site and other announcements.  

## Managing API Keys

There are important new features available for creating the API key used when publishing items. The full documentation is currently in the [PowerShell docs github repo](https://github.com/PowerShell/PowerShell-Docs/blob/psgallery-preview/gallery/how-to/managing-profile/creating-APIkeys.md). 

Publishing keys are never displayed in the latest UI, and are only available to be copied immediately after they are generated. This is covered in the [Creating API Keys](https://github.com/PowerShell/PowerShell-Docs/blob/psgallery-preview/gallery/how-to/managing-profile/creating-APIkeys.md) documentation. 

Any API key associated with your account will work when publishing to either PowerShellGallery.com or Preview.PowershellGallery.com. 

__Important note:__ If you have published items to PowerShellGallery.com, you have an existing Full Access API key that has no expiration. For security reasons, the new API key management system will not create keys with no expiration. If you delete the Full Access API key using the Preview Powershell Gallery UI, you can only re-create it using PowerShellGallery.com. That will  only be true until we switch over to the new, more secure system, at which time you will not be able to create any key that has no expiration date. 
