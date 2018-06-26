---
ms.date:  06/21/18
contributor:  JKeithB
keywords:  gallery,powershell,cmdlet,psgallery
title:  Preview PowerShell Gallery Release Notes
---
# Internal Preview PowerShell Gallery Release Notes

## What has changed?
The PowerShell Gallery site is being updated to a new look, with some new features. Today, the changes are internally available via [https://Preview.PoshtestGallery.Com](https://Preview.PoshtestGallery.Com). 

**Please try out our new site and give us feedback!**

We started this work to improve the performance of acquiring items from the PowerShell Gallery, particularly outside the US. While we were making the change, we are taking the opportunity to add security features and update the look of the PowerShell Gallery to a more current design. 

Most of the new features come from the latest NuGet server code, as we are aligning more with them. Some of the features in this preview include:

* Improved download performance provided via CDN
* Enhanced security for publishers, including support for 2FA, multiple publishing keys
* Account management support for changing email address or login account
* Direct download of items (as .Nupkg files)
* UI updated to be more responsive 

The preview.poshtestgallery.com site is an internal testing location, so the initial internal preview will not affect users who of PowerShellGallery.com. 

We will be releasing a public preview soon, which shares the same storage as PowerShellGallery.com. All items in the public preview will also be available in the production PowerShellGallery site. 

Once we have enough testing of these changes, the original UI will be retired and everyone will get the new experience. That change is expected this fall (2018).

## How to get started?

The internal preview site url is at [https://preview.poshtestgallery.com](https://preview.poshtestgallery.com). 
Start by browsing to the site and checking out the new look.

It is important to note that the preview.poshtestgallery.com site is an internal testing location. There is very little content in both this site and the production PowerShell Gallery. The main exception are PowerShellGet and the Azure modules published by the Azure SDK team. 

To use this new site with PowerShellGet, you must create register this as a PS Repository, then specify that repository with the PowerShellGet cmdlets:

```powershell
Register-PSRepository -Name PrivatePreview -SourceLocation https://preview.poshtestgallery.com/api/v2 
Find-Module DSC* -Repository PrivatePreview
Install-Module DSCTestModule -Repository PrivatePreview -Verbose
```

**Note:** There are issues listed below about errors if you install any of the  modules that exist in both PowerShellGallery.com and the test environment. 

If you want to publish something to the internal preview, please read the "Publishing to the Preview" instructions, below. 

## What would we like you to try out?
Some of the newer features that we want people to try out are:

* Help us validate CDN by downloading large modules, or modules with many dependencies. Azure modules are a good place to start.  
* The new PowerShell Gallery Account management allows changing the email address, or the MSA account associated with a Gallery user. You should also check out notifications generated when your module is updated.
* Please try publishing (important instructions are below). If you have multiple modules, try using different API keys to publish them. 
* We want feedback for the default view on the new page for individual items (like Azure). The new page collapses out much of the detail shown previously – but are we showing what is needed most?

## What is not working?

The following things are known to not work as expected. 
If you encounter something that is not listed here, please create an entry in our [issues list](https://github.com/PowerShell/PowerShellGallery/issues). 

The list is organized generally by the page where the issue will most likely be encountered.

* Most the PowerShellGallery content is missing: 
The preview.poshtestgallery.com site is an internal testing location. There is very little content in both this site and the production PowerShell Gallery. The Azure modules published by the Azure SDK team are available here. 
* I get failures trying to install the Azure modules from this site:
When you try to re-install a module from a new location, you will need to specify "-Force". 
As an example, the same versions of the Azure SDK team's modules are on both preview.poshtestgallery.com and powershellgallery.com.
If you try to install the same version of an item that you already have, install-module will skip it.
* Installation option for Azure Automation is not yet working: 
Three installation options are listed on the details page for any item. The Azure Automation option replaces the previous "Deploy to Azure Automation", but it is not currently functioning.
* The commenting system does not work for preview.poshtestgallery.com:
At the bottom of each item detail page is a "Comments" section. That section is provided by the LiveFyre service. Since preview.poshtestgallery.com is a temporary environment, we have not registered it with LiveFyre. As a result, the commenting system does not currently accept any sign-in or updates. This is expected to be resolved when during our public preview.
* The statistics page is still under construction: 
The pages that provide download statistics for all items and for individual items are still under construction. We expect them to function properly, but they have not yet been updated with the same look as the other pages. 
* Recent fixes in Deploy to Azure Automation are not in the preview:
The PowerShell Gallery was recently updated to fix problems where items with complex dependency trees could not be deployed to Azure Automation. This change has not yet been applied to the Preview gallery.


## How to publish a module to the private preview Gallery?

**IMPORTANT NOTE:** We greatly appreciate help testing the internal preview Gallery, but it is our test environment. As we point out on the site's banner, we will be deleting content and accounts from this gallery once the preview period is over (September, at the earliest). We will try to give ample warning by changing the banner when we are getting close, and sending out an email to everyone we can reach who has created a new account. 

As mentioned previously, the preview.poshtestgallery.com site is completely separate from PowerShellGallery.com. Very few people have accounts in this environment, so you will likely need to create your account here. Click on the "sign in" link, and follow the instructions to create your account, and let us know if you have any difficulties.  

Once you have created your account, please take a moment to check out the new features for managing accounts and publishing keys. 

You will need to upgrade your version of NuGet.exe to at least 4.1.0. You can upgrade by downloading NuGet.exe from https://www.nuget.org/downloads (latest version: https://dist.nuget.org/win-x86-commandline/latest/nuget.exe), and saving it within the PowerShellGet folder or under one of the paths specified in PATH environment variable value. We will be releasing an updated version of PowerShellGet shortly that will force this update, but for now this must be done manually. 

After you have done this, you can publish normally by specifying "-Repository PrivatePreview". 

## Advanced users please try this...

Users who are willing should consider unregistering the default (PSGallery) repository, and using the internal preview as their primary or default PSRepository.  

It is not possible to change the registration for PSGallery to go to a different URL. Instead, what you must do is unregister PSGallery, and leaving only GalleryPreview registered, as in:

```powershell
Unregister-psrepository –Name PSGallery
Get-PSRepository
```

If the preview gallery is the only repository listed, it will be the default.  Once that is done, Find-, Install-, and Save-Module will work with Preview gallery without having to specify the Repository. Publishers will still need to specify –Repository, because Publish-Module only allows the PSGallery to be the default. 

To revert to using the production site, please use:
 
```powershell 
Unregister-PSRepository –Name InternalPreview
Register-PSRepository –Default
```

Please note: The preview URL will go away when we transition the changes in preview to the production PowerShell Gallery, which will happen in the fall of 2018. This will break any automation that uses the preview URL as its target. We will, of course, be communicating that change via the preview site and other announcements.  
