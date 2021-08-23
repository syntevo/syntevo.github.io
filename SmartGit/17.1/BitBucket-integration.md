# Bitbucket integration

SmartGit integrates Bitbucket workflows in various places, very similar
to the
[GitHub](GitHub-integration.md#GitHubintegration-github)
integration. Some behavior can be customized by [system properties](System-Properties.md#smartgitrevertcommitmessagetemplatebitbucket)
.

### Setup

To set up the Bitbucket integration, go to **Preferences**, section
**Hosting Providers** and use **Add** there. In the **Add Hosting
Provider** dialog, have **Bitbucket** selected and invoke **Generate API
token**. This should open up your default web browser where you will
have to confirm by **Grant**.

![](attachments/10715362/10715364.png)

Once you have confirmed this page, you will be redirected to
*[syntevo.com](http://syntevo.com)*, where the generated access code
will be displayed. Copy&paste this code into SmartGit's **Generate API
Token** dialog and invoke **Authenticate**. The code will be used to
create an *application access token* which will be used to populate the
**Token** field. Finally, confirm the **Add Hosting Provider** dialog
using **Add**.

Once you have authorized SmartGit, it will show up in your GitHub
**Settings**, section **OAuth**. If you need to rerun through the
Authorization process outlined above, you have to **Revoke** access
there first and start over.

![](attachments/10715362/10715363.png)

 


