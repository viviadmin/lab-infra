# Scripts

Standalone scripts that don't yet justify an Ansible role. Each script:

- Has a `#!/usr/bin/env bash` shebang and a header comment with usage + exit codes
- Is idempotent where reasonable
- Logs to stderr, sends primary output to stdout
- Passes `shellcheck`

Scripts are promoted to Ansible roles once they're stable enough to be idempotent
across hosts. Until then, they live here.

## Index

_Empty — first script lands with D11 (bash basics)._