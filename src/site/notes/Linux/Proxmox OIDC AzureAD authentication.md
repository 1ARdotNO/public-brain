---
{"dg-publish":true,"permalink":"/linux/proxmox-oidc-azure-ad-authentication/","tags":["proxmox","pve","azuread","public","office365","linux"],"noteIcon":"1"}
---


**Step 1** - Sign into Azure AD and click **App Registrations**.


![r/Proxmox - Proxmox OIDC Authentication Azure AD](https://preview.redd.it/wdhynmn5tco71.png?width=624&format=png&auto=webp&s=54f3a1ba29d530e693c8bd4d4c9d62706a9b22b9)

**Step 2** – Click **New Registration** add a name and one of your Proxmox Servers

![r/Proxmox - Proxmox OIDC Authentication Azure AD](https://preview.redd.it/nijwg6s6tco71.png?width=624&format=png&auto=webp&s=f0403320bd9782f5547bc6b261517b5955650785)

**Step 3** –Add all of your URL for your Proxmox Servers by clicking **Add URI** then Save.

![r/Proxmox - Proxmox OIDC Authentication Azure AD](https://preview.redd.it/37psk3s7tco71.png?width=624&format=png&auto=webp&s=7a225c3c55f9f7ae1af6afce9ef4082c41902b78)

**Step 4** – Click **Certificates & Secrets** then **New Client Secret** you can specify when you want the secret to expire. Make sure you save the Secret under **Value,** we will need this later.

![r/Proxmox - Proxmox OIDC Authentication Azure AD](https://preview.redd.it/uaz61jm8tco71.png?width=624&format=png&auto=webp&s=79bf3dd537f8c84f1c7cba1c5fca9aecc4f19402)

**Step 5** – Click **Overview** Copy the **Client ID** then click Endpoints

![r/Proxmox - Proxmox OIDC Authentication Azure AD](https://preview.redd.it/6e7ev8matco71.png?width=624&format=png&auto=webp&s=60cd84b632d3b66ad346a440839db1ee96f22769)

Copy the **OpenID Connect metadata document** link and remove **/.well-known/openid-configuration** this part from the link, so you end up with something like this [https://login.microsoftonline.com/{Your](https://login.microsoftonline.com/%7BYour) **Tenant ID}/v2.0**

![r/Proxmox - Proxmox OIDC Authentication Azure AD](https://preview.redd.it/gx7dxlwbtco71.png?width=624&format=png&auto=webp&s=5c8b6a222984eb3c33bd6b762504623f61b112ea)

**Step 6** – Go to Proxmox and **Authentication** – **Add** – **OpenID Connect** then add the values for Azure AD

![r/Proxmox - Proxmox OIDC Authentication Azure AD](https://preview.redd.it/v151apnctco71.png?width=624&format=png&auto=webp&s=cf69a38cfb974751cdb9dc2ce786d099baa87b7d)

Now sign out and sign in with your new **Realm** and you should be good to go. This should be pretty much the same if you’re using Okta, ADFS, or something else. I think the main thing you need to know is that Issuer URL is really looking for your OpenID Connect Metadata, and it’s auto appending **/.well-known/openid-configuration** to the URL so you don’t need to add it again.

Source: [Proxmox OIDC Authentication Azure AD : r/Proxmox](https://www.reddit.com/r/Proxmox/comments/pqxu2o/proxmox_oidc_authentication_azure_ad/)
