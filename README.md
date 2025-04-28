# GLAuth rocks

![Latest Version](https://img.shields.io/badge/dynamic/yaml?url=https%3A%2F%2Fraw.githubusercontent.com%2Fcanonical%2Fglauth-rock%2Fmain%2Frockcraft.yaml&query=%24.version&label=Release&color=red)
![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?logo=postgresql&logoColor=white)
[![License](https://img.shields.io/github/license/canonical/glauth-rock?label=License)](https://github.com/canonical/glauth-rock/blob/main/LICENSE)

[![Build](https://img.shields.io/github/actions/workflow/status/canonical/glauth-rock/push_main.yaml?label=Build)](https://github.com/canonical/glauth-rock/actions/workflows/push_main.yaml)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit)](https://github.com/pre-commit/pre-commit)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-%23FE5196.svg)](https://conventionalcommits.org)

[Rocks](https://canonical-rockcraft.readthedocs-hosted.com/en/latest/explanation/rocks/#rocks-explanation)
for [GLAuth](https://github.com/glauth/glauth).

This repository holds all the necessary files to build rocks for the upstream
GLAuth LDAP server. The GLAuth rock is used by
the [glauth-k8s-operator](https://github.com/canonical/glauth-k8s-operator)
charm.

The GLAuth rock also applies patches to fix issues in the upstream project such as https://github.com/glauth/glauth/pull/450. When the patches
are merged upstream, they will be removed and pulled directly from the original source.

## Security

Please see [SECURITY.md](https://github.com/canonical/glauth-rock/blob/main/SECURITY.md)
for guidelines on reporting security issues.

## Contributing

Please refer to the [CONTRIBUTING](CONTRIBUTING.md) for developer guidance.
