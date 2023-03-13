---
{"dg-publish":true,"permalink":"/software/giscus-github-discussions-powered-comments/","tags":["public"],"noteIcon":"1"}
---

#Github 
URL :[giscus](https://giscus.app/)
reference from creator: [Introducing giscus | laymonage](https://laymonage.com/posts/giscus)

# about
giscus is a comment system for embedding in your website that uses github discussions as the comment backend. 

# [[Software/Obsidian\|Obsidian]]

Currently looking into how to implement this in digital garden,
[Feature: comments on pages · Issue #199 · oleeskild/obsidian-digital-garden · GitHub](https://github.com/oleeskild/obsidian-digital-garden/issues/199)

### Issue #199
### 

**[OvrAp3x](https://github.com/OvrAp3x)** commented [8 minutes ago](https://github.com/oleeskild/obsidian-digital-garden/issues/199#issue-1589161268) • edited 

I have been looking into implementing some comments feature for the pages.

I have tested with [https://giscus.app/](https://giscus.app/) which uses gihub discussions as the backend for the comment field.

configured as such  
[![image](/img/user/attachments/image.png)](https://user-images.githubusercontent.com/14344702/219622657-db5a2194-e57e-41e1-9c31-78c16012ed6c.png)

Then taking the snippet created from the giscus app and pasting it at the bottom of the .md file and due to the feature of rendering html in digital garden already, this causes the comment field to be loaded and it works great :-)  
Example: [https://1ar.no/zero-tier-and-github-actions-zero-tier/](https://1ar.no/zero-tier-and-github-actions-zero-tier/)  
source: [https://github.com/OvrAp3x/public-brain/blob/main/src/site/notes/ZeroTier%20and%20Github%20Actions%20%E2%80%93%20ZeroTier.md](https://github.com/OvrAp3x/public-brain/blob/main/src/site/notes/ZeroTier%20and%20Github%20Actions%20%E2%80%93%20ZeroTier.md)  
backend: [https://github.com/OvrAp3x/public-brain/discussions](https://github.com/OvrAp3x/public-brain/discussions)

What I am struggling with is how to set it up som that in the settings in obsidian there is a field that the giscus snippet can be pasted in, and automatically appended to the file when it is published.  
Any pointers or help about how this can be accomplished?

Reference for how to solve this, provided by Ole Eskil in the issue.

[Adding custom components](https://dg-docs.ole.dev/advanced/adding-custom-components)