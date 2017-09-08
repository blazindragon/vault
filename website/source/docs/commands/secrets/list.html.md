---
layout: "docs"
page_title: "secrets list - Command"
sidebar_current: "docs-commands-secrets-list"
description: |-
  The "secrets list" command lists the enabled secret engines on the Vault
  server. This command also outputs information about the enabled path including
  configured TTLs and human-friendly descriptions. A TTL of "system" indicates
  that the system default is in use.
---

# secrets list

The `secrets list` command lists the enabled secret engines on the Vault server.
This command also outputs information about the enabled path including
configured TTLs and human-friendly descriptions. A TTL of "system" indicates
that the system default is in use.

## Examples

List all enabled secrets engines:

```text
$ vault secrets list
Path          Type         Description
----          ----         -----------
cubbyhole/    cubbyhole    per-token private secret storage
secret/       generic      generic secret storage
sys/          system       system endpoints used for control, policy and debugging
```

List all enabled secrets engines with detailed output:

```text
$ vault secrets list -detailed
Path          Type         Accessor              Plugin    Default TTL    Max TTL    Force No Cache    Replication    Description
----          ----         --------              ------    -----------    -------    --------------    -----------    -----------
cubbyhole/    cubbyhole    cubbyhole_10fbb584    n/a       n/a            n/a        false             local          per-token private secret storage
secret/       generic      generic_167ce199      n/a       system         system     false             replicated     generic secret storage
sys/          system       system_a9fd745d       n/a       n/a            n/a        false             replicated     system endpoints used for control, policy and debugging
```

## Usage

The following flags are available in addition to the [standard set of
flags](/docs/commands/index.html) included on all commands.

- `-detailed` `(bool: false)` - Print detailed information such as configuration
  and replication status about each secrets engine.