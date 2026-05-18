# app-updates

Public auto-update feeds and binaries for macOS applications by Stepan Solodnev (Sleepy Coach, Inc).

Each application has its own folder containing a Sparkle `appcast.xml` manifest and the released `.zip` builds.

## Apps

| App | Bundle ID | Feed URL |
|---|---|---|
| DictationApp | `com.stepan.dictation*` | [`dictationapp/appcast.xml`](dictationapp/appcast.xml) |

## How it works

Each shipped build embeds a `SUFeedURL` in its `Info.plist` pointing at this repo's `appcast.xml` for that app. On launch, Sparkle fetches the manifest, finds the highest `sparkle:version`, compares against the running build, and offers an update if a newer one exists.

`.zip` payloads are signed with an EdDSA key whose **public** half is embedded in the app. Sparkle refuses to install a payload whose signature doesn't match — so this repo being public is fine: an attacker who modifies a `.zip` here cannot forge the signature.

## Release workflow

See [`docs/RELEASE_RUNBOOK.md`](https://github.com/Solodnev/dictationapp-cloud-mvp/blob/main/docs/reference/RELEASE_RUNBOOK.md) in the main project repo (private).
