# Metanorma Build Scripts

This repository contains:
 - `*.[sh|ps1|bat]` - different scripts used during build as part of CI workflow
 - `default.xml` - manifest for [`repo`](https://gerrit.googlesource.com/git-repo/+/refs/heads/master/README.md) tool, more details in [`ci-master README.md`](https://github.com/metanorma/ci-master/blob/master/README.md)
 - `ci-master` - CI configuration which consumed by

## `default.xml`

To keep `default.xml` up-to-date use [`gh-repo-manifest`](https://github.com/metanorma/ci-master/blob/master/bin/gh-repo-manifest)

## Anatomy of `ci-master`

Primary config file are [`ci-master/config/ci.yml`](ci-master/config/ci.yml)

```yml
repos:
  metanorma-cli:
    .github/workflows/ubuntu.yml: gh-actions/master/ubuntu.yml
    .github/workflows/macos.yml: gh-actions/master/macos.yml
    .github/workflows/windows.yml: gh-actions/master/windows.yml
  ...
```

Inside of `repo` object: keys are repository names i.e. `metanorma-cli`, they match to `path` attribute in [`default.xml`](./default.xml)

Keys inside of `metanorma-cli` object are just mapping from `ci-master/config/*` to file path in `$repository-name` reposity

### default.xml

This file generated by [`gh-repo-manifest`](https://github.com/metanorma/ci-master/blob/master/bin/gh-repo-manifest) and it's format described [here](https://gerrit.googlesource.com/git-repo/+/refs/heads/master/docs/manifest-format.md)