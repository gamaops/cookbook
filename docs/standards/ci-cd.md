# CI/CD

Every CI/CD must be able to read version changes from commit messages. These version changes must be only valid from PRs and not from normal commits. We implemented the [Semantic Versioning](https://semver.org/) standard and you can annotate your PR commit message with the following labels (and they will affect the version only when the merge is to the `master` branch).

* **\#version:[version]** - Upgrades a version like major, minor, patch, premajor, etc.
* **\#preid:[preid]** - Upgrades a pre version with a preid like alpha, beta, rc.

**Examples**

* **\#version:patch**
* **\#preid:rc**