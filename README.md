# PigeonOS releases

Signed update bundles for Pigeon Clock and Pigeon Marquee. Each [release](../../releases) contains:

| File | What it is |
| --- | --- |
| `pigeon_<version>_<commit>.zip` | The PigeonOS app for that version |
| `latest.json` | Version, commit, download URL, SHA-256 and size of the bundle |
| `latest.json.sig` | SSH signature of `latest.json` (namespace `pigeon-release`) |

A Pigeon installs a release only if `latest.json` is signed by the release key built into it, the version is newer than what it runs, and the bundle matches the SHA-256 in the signed manifest. Nothing here is trusted on its own.

To check a release by hand:

```bash
ssh-keygen -Y verify -f release_signers -I pigeon-release -n pigeon-release -s latest.json.sig < latest.json
shasum -a 256 pigeon_*.zip
```

`release_signers` is the public key below.

```
pigeon-release namespaces="pigeon-release" ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIFyPWG2nHCOGNUuca09nxQVOW7ZYMQhWel7D6oZLn+Mh
```
