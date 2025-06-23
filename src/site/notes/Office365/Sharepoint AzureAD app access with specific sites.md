---
{"dg-publish":true,"permalink":"/office365/sharepoint-azure-ad-app-access-with-specific-sites/","tags":["public","azuread","office365","sharepoint","gemini"],"noteIcon":"1"}
---

# Background
When giving app access to sharepoint in [[AzureAD\|AzureAD]] it by default gives it to all sites, this is in most cases not prefered as you could have sensitive sites that you do not want the integrated app to have access to. In my case, I wanted to pass some specific sites to Gemini's RAG engine.
# About
The sites.selected permission will help fix this, it allows you to set permissions per sharepoint site. 

## How to Control App Access to a Specific SharePoint Site Collection

### 🔐 1. Assign `Sites.Selected` permission

- In **Azure AD** → **App Registration** → **API Permissions**, add the **Microsoft Graph** permission:  
    `Sites.Selected` (Application-level).
    
- **Grant admin consent**.  
    By default, this allows **no access** to any site collection
    
### ⚙️ 2. Grant site-specific access via Graph API

As a SharePoint admin, use the Microsoft Graph endpoint:

> [!NOTE] Tip! Use graph explorer
>[Graph-explorer](https://developer.microsoft.com/en-us/graph/graph-explorer)

```
POST https://graph.microsoft.com/v1.0/sites/contoso.sharepoint.com:/sites/demo:/permissions
Content-Type: application/json

{
  "roles": ["write"],
  "grantedToIdentities": [
    {
      "application": {
        "id": "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
        "displayName": "Foo App"
      }
    }
  ]
}
```

- `roles`: Choose permission level—`read`, `write`, `manage`, or `fullcontrol`.
    
- `siteId`: Can be expressed as the site’s hostname and relative path, for example:  
    `/sites/demo` 
- Once granted, the app can access **only** that site using the assigned role.
    
### 📘 3. Use permissions in your application

- The app now calls Graph or SharePoint REST/CSOM only on the permitted site.
- If accessing others, you'll get **403 Forbidden** [devblogs.microsoft.com+8devblogs.microsoft.com+8learn.microsoft.com+8](https://devblogs.microsoft.com/microsoft365dev/controlling-app-access-on-specific-sharepoint-site-collections/?utm_source=chatgpt.com)[techcommunity.microsoft.com](https://techcommunity.microsoft.com/blog/spblog/develop-applications-that-use-sites-selected-permissions-for-spo-sites-/3790476?utm_source=chatgpt.com).
- New delegated support exists: if the app also requests **delegated** `Sites.Selected`, call permission via `/permissions` remains the same [devblogs.microsoft.com+7devblogs.microsoft.com+7learn.microsoft.com+7](https://devblogs.microsoft.com/microsoft365dev/sharepoint-now-supports-delegated-sites-selected-authentication/?utm_source=chatgpt.com).
    

---

### ✅ 4. (Optional) Update permissions

- To **add/revoke** access, rerun the same POST (to add) or issue a DELETE against the specific permission ID [learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/1855689/restrict-app-access-of-graph-apis-to-specific-site?utm_source=chatgpt.com).
    
