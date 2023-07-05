# On-premise License Server

To monitor seat usage for a large number of users, it may be convenient to install our *On-premise License Server*.
This will be especially important if the SmartGit installations of your users are not allowed to connect to our central cloud license server.

## Requirements

To run our on-premise server, only Docker is required. This document describes how to setup the *On-premise License Server* in a plain docker environment. Running the *On-premise License Server* in a kubernetes environment will also work, but we cannot provide guidance on how to setup it (as this will vary depending on your environment). Please also note, by default the *On-premise License Server* uses an embedded database that will store data in a volume. Running multiple instances of the *On-premise License Server* in a kubernetes environment is not supported.

## Server-side installation

1. Contact sales@syntevo.com and provide a short explanation of your environment and SmartGit setup to understand whether an on-premise license server will be appropriate for your company.
  
2. If appropriate, you will receive a new *on-premise license file*
  
4. You need *GitHub credentials* to access the [GitHub packages](https://github.com/syntdev/license-server/pkgs/container/license-opserver). Please let us know the username so we can grant access.

5. Create a GitHub Personal Access Token to log in with Docker:

   1. Go to https://github.com/settings/tokens

   2. Click on **Generate Token** and select **Generate new token (classic)**

   3. Configure only the **read:packages** scope

7. From the command line, log in to the GitHub Docker repository:

   ```
   docker login ghcr.io -u <username> -p <pat>
   ```

   For the above command, replace `<username>` with your GitHub username and `<pat>` with the Personal Access Token you have just created.

8. Pull the Docker image:

   ```
   docker pull ghcr.io/syntdev/license-opserver:development
   ```

9. Prepare host directories for the Docker volumes

   1. On the target server where the Docker image will be run, create a top-level directory `<license-server-root>` which will contain the persistent data of the license server, for example, `/var/syntevo-license-server`.

   2. In this directory, create a sub-directory named `licenses`.

   3. Put the *on-premise license file* you have received from us into this directory. Use a reasonable name that reflects the product, e.g., `smartgit` in the case of a SmartGit license.

10. Start the license server:

   ```
   docker run --restart unless-stopped --name syntevo-license-server -d -v <license-server-root>/data:/data -v <license-server-root>/licenses:/licenses -p 8080:8080 ghcr.io/syntdev/license-opserver:latest
   ```

   For the above command, replace `<license-server-root>` with the actual top-level directory, for example:

   ```
   docker run --restart unless-stopped --name syntevo-license-server -d -v /var/syntevo-license-server/data:/data -v /var/syntevo-license-server/licenses:/licenses -p 8080:8080 ghcr.io/syntdev/license-opserver:development
   ```

11. Confirm that the license server has been properly started:

   ```
   docker ps | grep syntevo-license-server
   ```

#### Note
> The license files from the `licenses` directory will only be registered on startup of the license server. When applying changes to this directory, such as updating a license file, the container must be restarted:
> 
> ```
> docker stop syntevo-license-server
> docker rm syntevo-license-server
> docker run --restart unless-stopped --name syntevo-license-server -d -v <license-server-root>/data:/data -v <license-server-root>/licenses:/licenses -p 8080:8080 ghcr.io/syntdev/license-opserver:development
> ```

## SmartGit Setup

### Configuration by system property

We recommend deploying SmartGit with the [system property](System-Properties.md) `smartgit.opLicenseServer.url` pre-configured, so the license server will be contacted automatically on startup. For example:

```
smartgit.opLicenseServer.url=http://localhost:8080/v1
```

### Configuration during Setup

If required, users can configure the license server on-the-fly during setup:

1. In the Setup wizard, on the **License** page, select **Register existing license**.

2. In the lower right area of the wizard, click **Have an on-premise license server**.

3. For the upcoming **License Server URL** text field, enter the URL of the license server, e.g., `http://localhost:8080/v1`.

### Configuration after Setup

If SmartGit has already been started in evaluation mode and you want to switch to the license server, invoke **Help|Register** and follow the instructions from the above section.

