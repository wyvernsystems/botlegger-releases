# BotLegger 0.19.0 security report

**All 10 checks passed.** 25 known exceptions were reviewed and kept (6 low risk, 19 no risk); they are listed at the end.

Built from commit `d1430f22ce6c` on 2026-11-24. Every check ran on the release's own commit and files, and the release is not published unless all of them pass.

## Checks

| Check | Tool | Result |
|-------|------|--------|
| Leaked credentials anywhere in the git history | gitleaks 8.30.1 | Passed |
| Dependency licences, sources, and bans | cargo-deny 0.20.2 | Passed |
| Known vulnerabilities in Rust dependencies | cargo-audit 0.22.2 | Passed |
| Known vulnerabilities in Dart and account-service dependencies | osv-scanner 2.7.0 | Passed |
| Static analysis of our own code and workflows | semgrep 1.181.0 | Passed |
| GitHub Actions workflow audit | zizmor 1.31.1 | Passed |
| Bundled program versions match everywhere they are pinned | pins | Passed |
| Model stream parser fuzzing | fuzz | Passed |
| Signatures, notarization, and binary hardening of the release files | verify_artifacts.py | Passed |
| Anti-virus engines' verdict on every release file | VirusTotal | Passed |

## Release files

| File | SHA-256 | Signature | Hardening | VirusTotal |
|------|---------|-----------|-----------|------------|
| `BotLegger_0.19.0_linux_x86_64.tar.gz` | `f747f934d2a35f878567cc807079d7f97b45b0781520371c337da499284a7f2c` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO; 11 bundled libraries and helpers also checked | [0 of 62 engines flag it](https://www.virustotal.com/gui/file/f747f934d2a35f878567cc807079d7f97b45b0781520371c337da499284a7f2c) |
| `BotLegger_0.19.0_universal.dmg` | `cc39c8af48df1bb2653801fbf86a605d176cc6f369d6b87c910285e10ba5b019` | Developer ID (team 5S6TA8TSAC), notarized by Apple, ticket stapled, hardened runtime | PIE, stack canary | [0 of 46 engines flag it](https://www.virustotal.com/gui/file/cc39c8af48df1bb2653801fbf86a605d176cc6f369d6b87c910285e10ba5b019) |
| `BotLegger_0.19.0_windows_x86_64.zip` | `e4863f6d3e12430cc975802d4ed3d7cc66f5b9b279a24ea686ba1292e2eedd5f` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP; 15 bundled libraries and helpers also checked | [0 of 64 engines flag it](https://www.virustotal.com/gui/file/e4863f6d3e12430cc975802d4ed3d7cc66f5b9b279a24ea686ba1292e2eedd5f) |
| `BotLegger_0.19.0_windows_x86_64_setup.exe` | `2e25ab2173c550df0089b3175210c7feba4c75d5e28816e459b63f05abca7181` | unsigned (SmartScreen warns on first launch) | BotLegger_0.19.0_windows_x86_64_setup.exe: ASLR, DEP | [0 of 68 engines flag it](https://www.virustotal.com/gui/file/2e25ab2173c550df0089b3175210c7feba4c75d5e28816e459b63f05abca7181) |
| `bot-linux-x86_64.tar.gz` | `55057584dff711834125b1a4848d088f9e7bbaaee2b13d3c668eb36fb397b9b1` | unsigned archive; verify the SHA-256 in sha256.sum | bot: PIE, NX, full RELRO, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/55057584dff711834125b1a4848d088f9e7bbaaee2b13d3c668eb36fb397b9b1) |
| `bot-tui-aarch64-apple-darwin.tar.xz` | `794714b5743b59195aac159f9fbc0dc255f11b9d6f685671ef1efe5299c59c49` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/794714b5743b59195aac159f9fbc0dc255f11b9d6f685671ef1efe5299c59c49) |
| `bot-tui-x86_64-apple-darwin.tar.xz` | `925510e9b84683d4fe4c4337da5ddbb6a2b34368ebb34b44a4015376ff5c746d` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/925510e9b84683d4fe4c4337da5ddbb6a2b34368ebb34b44a4015376ff5c746d) |
| `bot-tui-x86_64-pc-windows-msvc.zip` | `4e3cab8b13c56aec9e62a34744d4ac239438fc4ef0b8e78c8cef33f47598b0a7` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP | [0 of 62 engines flag it](https://www.virustotal.com/gui/file/4e3cab8b13c56aec9e62a34744d4ac239438fc4ef0b8e78c8cef33f47598b0a7) |
| `bot-tui-x86_64-unknown-linux-gnu.tar.xz` | `c9092d5ceaefda47b9ac0338b6fb31ef8497d8246e8744684315036fc5e49dbb` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO, stack canary | [0 of 60 engines flag it](https://www.virustotal.com/gui/file/c9092d5ceaefda47b9ac0338b6fb31ef8497d8246e8744684315036fc5e49dbb) |
| `ggml-small-q5_1.bin` | `ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb` | data file, not a program; the apps accept only this SHA-256 | not applicable | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb) |

## Command-line installer scripts

Text scripts that download the command-line archives above and check their SHA-256. They are made from the previous release's scripts, and the release tooling refuses any change other than the version, download address, and checksum lines.

| File | SHA-256 |
|------|---------|
| `bot-tui-installer.ps1` | `72ae23ff7e6426a5cb686fecf1312ba44462d630a4d25b0167f37ff25bf0522d` |
| `bot-tui-installer.sh` | `30c8705810c3248300342f9511eec3e5bbf90216241ae80c4fb35cd042b397fb` |

## Known exceptions

Scanners flag patterns, and some of what they flag is harmless, such as made-up credentials that tests use to check secrets are hidden. 25 known exceptions were reviewed and kept (6 low risk, 19 no risk). Each is looked at again by its review date, and nothing above medium risk is ever accepted: anything riskier is fixed. Components are described rather than named, so this list is not a map of what to attack.

| Kind | Risk | Count | Why it is kept | Review by |
|------|------|-------|----------------|-----------|
| Build workflow | low | 1 | A build step runs a programming toolchain's official installer, downloaded over an encrypted connection, and only when the toolchain is missing. The risk rests on that vendor's own download site; changing it would break the release build. | 2027-11-07 |
| Build workflow | low | 1 | A build step writes fixed values and the build machine's own install paths into the build environment; no outside input reaches it. | 2027-11-07 |
| Build workflow | low | 1 | Build commands are inserted from the release tool's own configuration in the repository, never from outside input such as issue or pull request text. | 2027-11-07 |
| Build workflow | low | 1 | The build machine image is chosen and pinned by the release tool's own plan in the repository; the workflow only passes that choice along. | 2027-11-07 |
| Third-party code | low | 1 | A widely used third-party library whose maintainers stopped maintaining it. It has no known vulnerability; we are planning its replacement and review this again within three months. | 2027-02-16 |
| Third-party licence | low | 1 | A third-party library under a licence outside our default list. We use it unmodified and ship its notice, which is all that licence asks; replacing it would break a feature. | 2027-11-07 |
| Test data | none | 13 | Made-up credentials in automated tests that check secrets are hidden or refused; none ever worked anywhere. | 2027-11-07 |
| Build workflow | none | 1 | A value inserted into a build command comes from a fixed list written in the same workflow, so no outside input can reach it. | 2027-11-07 |
| Build workflow | none | 1 | The build passes its own credentials to build steps the way the build service documents; the rule flags every such use, safe or not. | 2027-11-07 |
| Generated data | none | 1 | Checksums of generated files that look like secrets by their shape only. | 2027-11-07 |
| Old history only | none | 1 | An example value from a third-party library's documentation, present only in old history; it never worked and is no longer in the code. | 2027-11-07 |
| Test data | none | 1 | A service's published documentation example, used in a test to check our request signing matches theirs; it never worked anywhere. | 2027-11-07 |
| Test data | none | 1 | Made-up credential accepted only by a fake service the tests start on the test machine; it never worked anywhere. | 2027-11-07 |

## Verify this report

`security-report.md.sig` is the release key's Ed25519 signature over this file's exact bytes, the key every installed app trusts for its updates. With OpenSSL 3:

```bash
printf '%s' 'EaXGTEjOxvn525qWsmalE7PbGimGX58ZgfWU6khnn4k=' | base64 -d > key.raw
{ printf '\x30\x2a\x30\x05\x06\x03\x2b\x65\x70\x03\x21\x00'; cat key.raw; } > key.der
base64 -d security-report.md.sig > security-report.md.sigbin
openssl pkeyutl -verify -pubin -keyform DER -inkey key.der -rawin -in security-report.md -sigfile security-report.md.sigbin
```

Every release's report is attached to that release at <https://github.com/wyvernsystems/botlegger-releases/releases>.
