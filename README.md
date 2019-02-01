# Ubuntu

This is a library of Ubuntu builds for Singularity images hosted on Singularity Static Registry. The following standard applies:

 - each `Singularity` file corresponds to a build
 - tags are supported based on the extension of the Singularity file, with an extensionless file corresponding to "latest"

## What can I find here?

The repository here serves the container under the namespace `singularityhub/centos`.

## How does this work?

We will submit this container to the (organizational) registry at 
[singularityhub/registry-org](https://www.github.com/singularityhub/registry-org)
for a final container uri corresponding to `https://singularityhub.github.io/registry-org/singularityhub/centos`. Specifically:

```
singularityhub/registry-org  --) the organization registry
singularityhub/centos        --) a container collection
```

then on GitHub pages:

```
singularityhub.github.io/registry-org                       --) the registry interface
singularityhub.github.io/registry-org/singularityhub/centos --) the added container
```

This works by way of the repository here (via the continuous integration)
building the container, uploading it to storage, and then opening (or updating)
a branch on the registry repository. The registry repository uses a 
[GitHub Action](https://www.github.com/vsoch/pull-request-action) that will
open a pull request whenever a branch is pushed.

For this particular example, the container namespace is a bit
redundant, but if the GitHub username was different from the organization, you
can see how it would be important to maintain this namespace. I've also thought
about having the main registry redirect to the GitHub pages of the container's Github
pages, but I don't want to introduce redirects yet.
