# Jenkins integration (only Standard window)

SmartGit will display Jenkins job results in the **My History** view of
*Standard* window, if configured.

## Configuration

The integration is configured in the repository's `.git/config`,
using `smartgit.jenkins.`-keys:

* `url`: the root URL of your Jenkins server
* `jobs`: a comma-separated list of Jenkins job names which should be queried

#### Example
>
>``` text
>[smartgit "jenkins"]
>   url = http://localhost:8080
>   jobs = tests,tests-gitimpl,tests-jgit
>```
