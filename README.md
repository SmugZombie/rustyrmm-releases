# RustyRMM agent releases

Signed builds of the RustyRMM agent, published by RustyRMM's release
pipeline. This repository contains no source code, only
[releases](../../releases).

Each release has:

| File | |
|---|---|
| `rmm-agent-<platform>-<arch>[.exe]` | Agent builds for Windows, macOS and Linux |
| `RustyRMM-Agent-<version>.pkg` | Signed macOS installer for MDM deployment |
| `manifest.json` | Versions, sizes, SHA-256 hashes and signatures (read by RustyRMM servers) |
| `SIGNATURES.txt` | The same signatures, human-readable |

RustyRMM servers pull new builds from here automatically:

```sh
RMM_RELEASE_GITHUB_REPO=SmugZombie/rustyrmm-releases   # no token needed
```

Every build is signed with an offline ed25519 key. Servers verify it against
their `RMM_UPDATE_PUBKEY` before importing it, and agents verify it again
before installing, so a build from any source that isn't signed with your
key is rejected.
