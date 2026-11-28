# BotLegger 0.24.0 security report

**All 10 checks passed.** 25 known exceptions were reviewed and kept (6 low risk, 19 no risk); they are listed at the end.

Built from commit `b32fd7f80677` on 2026-11-28. Every check ran on the release's own commit and files, and the release is not published unless all of them pass.

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
| `BotLegger_0.24.0_linux_x86_64.tar.gz` | `cc3a6d30b32abf726d99f8934cc8d728bf61b9cd4c7806064bf00eef11317a5a` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO; 11 bundled libraries and helpers also checked | [0 of 62 engines flag it](https://www.virustotal.com/gui/file/cc3a6d30b32abf726d99f8934cc8d728bf61b9cd4c7806064bf00eef11317a5a) |
| `BotLegger_0.24.0_universal.dmg` | `8555f06c2ae95375977e28df33e974365bc6d17fe2df421fd509fd10055877c7` | Developer ID (team 5S6TA8TSAC), notarized by Apple, ticket stapled, hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/8555f06c2ae95375977e28df33e974365bc6d17fe2df421fd509fd10055877c7) |
| `BotLegger_0.24.0_windows_x86_64.zip` | `3bf2ab6cc5d6af1fe0db6ae00b6cdf9f5aa9a3b961f3e30fe2f97fec6b5ed7e5` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP; 15 bundled libraries and helpers also checked | [0 of 65 engines flag it](https://www.virustotal.com/gui/file/3bf2ab6cc5d6af1fe0db6ae00b6cdf9f5aa9a3b961f3e30fe2f97fec6b5ed7e5) |
| `BotLegger_0.24.0_windows_x86_64_setup.exe` | `88043a9f8046ee2cf433c94ae39d89ea0fc987db04136d94d5cb2980e559a3b4` | unsigned (SmartScreen warns on first launch) | BotLegger_0.24.0_windows_x86_64_setup.exe: ASLR, DEP | [0 of 66 engines flag it](https://www.virustotal.com/gui/file/88043a9f8046ee2cf433c94ae39d89ea0fc987db04136d94d5cb2980e559a3b4) |
| `bot-linux-x86_64.tar.gz` | `9787811580ac57b7af2dfdbf1bd5d874c252889f241365d3242600010b1c3297` | unsigned archive; verify the SHA-256 in sha256.sum | bot: PIE, NX, full RELRO, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/9787811580ac57b7af2dfdbf1bd5d874c252889f241365d3242600010b1c3297) |
| `bot-tui-aarch64-apple-darwin.tar.xz` | `d6c6790611b455ee5529c8044b1028f0c36b227d84bf918f6fb3ad873e26ad1c` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/d6c6790611b455ee5529c8044b1028f0c36b227d84bf918f6fb3ad873e26ad1c) |
| `bot-tui-x86_64-apple-darwin.tar.xz` | `858fc2525f3ef28f1cea9996dc75b52f9b87f5c65b7379bfaf8a39accfeef4c8` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 62 engines flag it](https://www.virustotal.com/gui/file/858fc2525f3ef28f1cea9996dc75b52f9b87f5c65b7379bfaf8a39accfeef4c8) |
| `bot-tui-x86_64-pc-windows-msvc.zip` | `e38d49bd7b2d2391cb8f8e47d171c99897dac1d22a4cbea4369079f90578e045` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP | [0 of 64 engines flag it](https://www.virustotal.com/gui/file/e38d49bd7b2d2391cb8f8e47d171c99897dac1d22a4cbea4369079f90578e045) |
| `bot-tui-x86_64-unknown-linux-gnu.tar.xz` | `2bc07a83cc6b74ae23f2ee3b0f3cedac105abc99c6dbac77c163fd9e2f1e4f93` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO, stack canary | [0 of 60 engines flag it](https://www.virustotal.com/gui/file/2bc07a83cc6b74ae23f2ee3b0f3cedac105abc99c6dbac77c163fd9e2f1e4f93) |
| `ggml-small-q5_1.bin` | `ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb` | data file, not a program; the apps accept only this SHA-256 | not applicable | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb) |

## Command-line installer scripts

Text scripts that download the command-line archives above and check their SHA-256. They are made from the previous release's scripts, and the release tooling refuses any change other than the version, download address, and checksum lines.

| File | SHA-256 |
|------|---------|
| `bot-tui-installer.ps1` | `62c326f943c7cfc4a7e4d72aeeb9baefff1fcc2b7dbca2bb37275549c3bd0a2d` |
| `bot-tui-installer.sh` | `e51a845562663c922f01a3a100e5315ec8be28aaa0a5c51c7e22d894f65dd58f` |

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
