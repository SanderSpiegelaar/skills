# Triage Labels

Default mapping: the five canonical **state** roles from the `triage` skill use the same strings as GitHub labels (or local markdown `Status:` values). Edit the **Label in this repo** column only if your tracker already uses different names.

The skills refer to roles by canonical name; this table maps each role to the label string your tracker uses.

| Canonical role | Label in this repo | Meaning                                  |
| -------------- | ------------------ | ---------------------------------------- |
| `needs-triage`             | `needs-triage`       | Maintainer needs to evaluate this issue  |
| `needs-info`               | `needs-info`         | Waiting on reporter for more information |
| `ready-for-agent`          | `ready-for-agent`    | Fully specified, ready for an AFK agent  |
| `ready-for-human`          | `ready-for-human`    | Requires human implementation            |
| `wontfix`                  | `wontfix`            | Will not be actioned                     |

When a skill mentions a role (e.g. "apply the AFK-ready triage label"), use the corresponding **Label in this repo** string from this table.
