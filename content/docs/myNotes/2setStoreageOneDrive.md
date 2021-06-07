---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "2. Set Storage Onedrive"
linktitle: "2. Set Storage Onedrive"
summary:
date: 2021-06-07T16:04:47+07:00
lastmod: 2021-06-07T16:04:47+07:00
toc: true  # Show table of contents? true/false
type: book
weight: 2
---


You must have known that OneDrive for Business storage has a limitation of 1TB but what if you have utilized the full capacity (1TB). There is no such announcement for the same, but the limit is not 1TB.  **In this article, we will see how we can increase the storage capacity for OneDrive for Business up to 5TB through PowerShell.**

As per one of the Microsoft articles “**If your organization has a qualifying Office 365 plan and 5 or more users, you can change the storage space to more than 5TB**”. So as per this statement, we can get more than 5TB as well. That means the limitation is not 5TB as well.

Increasing the storage from 1TB to 5TB can be done with the help of your Microsoft 365 Administrator through PowerShell, but going beyond 5TB, you will need the help of Microsoft Support with justification and then it might get increased up to 25TB quota.


![Infographic](https://drive.google.com/uc?id=1M7NAsAb8673dFIH61mwRdPpK1wQ3boyt)

**Pre-requisites:**

1.  Download SharePoint Online Management Shell.
    **https://www.microsoft.com/en-us/download/details.aspx?id=35588
    **
2.  Connect to SharePoint Online through PowerShell.
    **_$adminUPN=”<the full email address of administrator account>”
    $orgName=”<name of your Office 365 organization>”_**![Connecting to SPO PowerShell](https://cdn-angbj.nitrocdn.com/shObXeyLxXflGAhcIcxEKCbyevxxnCNO/assets/static/optimized/rev-0abd59b/wp-content/uploads/2020/02/1-9.png)
    **_$userCredential = Get-Credential -UserName <the full email address of administrator account>
    _**This is prompt to enter Message, enter the admin account password and hit enter.![SPO Admin Credentials](https://cdn-angbj.nitrocdn.com/shObXeyLxXflGAhcIcxEKCbyevxxnCNO/assets/static/optimized/rev-0abd59b/wp-content/uploads/2020/02/2-11.png)**_
    Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
    _**You will be prompted to provide admin credentials.
    **_
    ![Connect SPO Site](https://cdn-angbj.nitrocdn.com/shObXeyLxXflGAhcIcxEKCbyevxxnCNO/assets/static/optimized/rev-0abd59b/wp-content/uploads/2020/02/3-11.png)_**

**Increasing the storage quota for OneDrive for Business:
**

1.  Check the current set quota for a user.
    **_Get-SPOSite -Identity <User’s OneDrive URL> | select $StorageQuota_**
    **Note: – Storage quota is in MB.**![Check Storage for a user](https://cdn-angbj.nitrocdn.com/shObXeyLxXflGAhcIcxEKCbyevxxnCNO/assets/static/optimized/rev-0abd59b/wp-content/uploads/2020/02/4-10.png)
2.  Change the storage quota for a specific user.
    **_Set-SPOSite -Identity <User’s OneDrive URL> -StorageQuota $StorageSize
    _Note: – Replace  _$StorageSize_  with 5242880 (MB) which is 5TB
    **
3.  To verify the change, run cmd  **_Get-SPOSite -Identity <User’s OneDrive URL> | select $StorageQuota
    ![Set storage for a user](https://cdn-angbj.nitrocdn.com/shObXeyLxXflGAhcIcxEKCbyevxxnCNO/assets/static/optimized/rev-0abd59b/wp-content/uploads/2020/02/5-10.png)
    _**
4.  You can also verify the same from  **Office 365 Admin Center > Active Users > Select User > OneDrive.**
    ![Verify ](https://cdn-angbj.nitrocdn.com/shObXeyLxXflGAhcIcxEKCbyevxxnCNO/assets/static/optimized/rev-0abd59b/wp-content/uploads/2020/02/6-9.png)

This article will help you to increase storage quota for OneDrive for Business up to 5TB without any need of calling Microsoft Support. If you need to increase it more than 5TB then you will need to take help from Microsoft Support with justification. Thanks!
