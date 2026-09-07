# Research Software Publishing Guide

gflab provides a shared home for the laboratory's research code, scientific software, and reproducible research artifacts. Members can create repositories, add project collaborators, and publish their work independently. These conventions support efficient collaboration and durable research outputs without introducing a mandatory approval process or a uniform CI requirement.

## Starting a Project

Create a repository from [research-template](https://github.com/gflab/research-template/generate), selecting `gflab` as the owner, or upload an existing project to a new repository. Prefer the method or software name as the repository name. A continuously maintained package generally belongs in one repository rather than a separate copy for each publication.

Choose public or private visibility according to the stage of the work. Project maintainers can grant collaborators Write access directly and provide additional permissions where needed for repository management or releases. Direct commits are appropriate for routine work; use pull requests when discussion or review would be useful. Adapt or remove template components freely. No particular programming language, directory layout, or CI system is required.

Use professional academic English for default repository descriptions, documentation, and release notes. Describe the project's purpose, primary maintainer and maintenance successor, installation, minimal execution command, data and model access, license, and maintenance status. Update `CITATION.cff` with the actual project and author metadata; omit publication details and DOIs that are not yet available.

## Publishing a Paper

1. Run the documented minimal example in a clean environment and record dependency versions. Explain which results can be reproduced and identify limitations arising from restricted data or computational resources.
2. Create a tag and GitHub Release, such as `v1.0.0`, for the commit used in the study. Describe the associated publication, execution procedure, and relevant data and model versions. Cite this fixed version rather than relying solely on the evolving `main` branch.
3. When a software DOI is useful, connect the repository to Zenodo, verify that the version has been archived, and add its DOI to the README and citation metadata. Zenodo integration is optional.
4. Link the repository from the publication page on the lab website and link the publication from the repository. Representative projects may be pinned to the organization profile.

Retain publication tags and releases unchanged. Publish corrections as new versions and explain the differences. Avoid deleting, transferring, or making published repositories private. When maintenance ends, document the status and archive the repository while preserving installation URLs. Arrange a maintenance handover before the responsible researcher leaves the project.

## Distributing Packages

Use the distribution channel that best serves the intended users: typically PyPI for Python, GitHub installation, CRAN, or Bioconductor for R, and `ghcr.io/gflab/<project>` for containers. GitHub serves as the shared source repository; packages do not need to move to GitHub Packages solely for consistency.

Members can create public and private GitHub Packages. The organization retains the default that packages inherit access from their source repository. Associate each package with its source repository and, after its first public release, verify installation or image retrieval without authentication where supported. Public source code does not automatically make a package public; verify package visibility explicitly. Configure maintainers and publishing authorization separately on external registries such as PyPI.

The template workflow uses read-only permissions. Grant only the permissions needed by an actual publishing job, such as `packages: write` for GHCR, `contents: write` for a GitHub Release, or `id-token: write` for trusted publishing. Third-party Actions may be used normally without a central approval process. Add publishing workflows when the project has selected its distribution channel.

## Licensing and Long-Term Access

Lab open-source code and software packages use the Apache License, Version 2.0 (`Apache-2.0`) by default. Projects created from the template retain this license and update copyright attribution as appropriate. Keep license metadata consistent across the README, `CITATION.cff`, and package metadata. Preserve applicable third-party licenses and notices, and respect different requirements imposed by upstream code or dependencies. Specify data and model licenses separately.

Store durable research artifacts in GitHub Releases, Zenodo, or suitable data and model repositories. Actions artifacts expire and must not be the sole source of supplementary material. Record stable access links, versions, and checksums where needed for large datasets and model weights.

Do not upload patient-level data to GitHub, including private repositories. Provide access instructions for public, synthetic, or appropriately authorized data instead. Members are encouraged to enable two-factor authentication; it is not currently a mandatory condition of organization membership.
