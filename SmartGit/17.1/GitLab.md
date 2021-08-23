# GitLab

SmartGit provides a basic GitLab integration which allows to query for a
list of projects/repositories on **Clone**.

### Setup

To set up the GitLab integration, go to **Preferences**, section
**Hosting Providers** and use **Add** there. In the **Add Hosting
Provider** dialog, have **GitLab** selected and enter a **Personal
Access Token** there.

If you do not already have a Personal Access Token for SmartGit, you can
create this token in your GitLab account **Settings**, section **Access
Tokens**. Be sure to have at least **api** scope enabled.

![](attachments/10715372/10715373.png)

This **Personal Access Token** can now be used to access the API as well
as authenticating to your GitLab repositories, where you can use it
instead of your main GitLab password.



When having 2-factor authentication enabled, a **Personal Access Token**
is even required. Your main GitLab can't be used anymore in this case.




