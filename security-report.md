# BotLegger 0.17.0 security report

**All 10 checks passed.** 25 known exceptions were reviewed and kept (6 low risk, 19 no risk); they are listed at the end.

Built from commit `0dc33b980598` on 2026-11-23. Every check ran on the release's own commit and files, and the release is not published unless all of them pass.

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
| `BotLegger_0.17.0_linux_x86_64.tar.gz` | `e004a1432b87359d1d4edf691b45e01cd865c4a94832289f8896a0f247f79c31` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO; 11 bundled libraries and helpers also checked | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/e004a1432b87359d1d4edf691b45e01cd865c4a94832289f8896a0f247f79c31) |
| `BotLegger_0.17.0_universal.dmg` | `3f9e5c88cec0469074665d301e529caa4785af2fbad0d6001b489e3efc50fb10` | Developer ID (team 5S6TA8TSAC), notarized by Apple, ticket stapled, hardened runtime | PIE, stack canary | [0 of 60 engines flag it](https://www.virustotal.com/gui/file/3f9e5c88cec0469074665d301e529caa4785af2fbad0d6001b489e3efc50fb10) |
| `BotLegger_0.17.0_windows_x86_64.zip` | `0ad2f4cd9f466baba73c699a55a1ff5d51211e371082df7a792b9f622a074b4b` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP; 15 bundled libraries and helpers also checked | [0 of 65 engines flag it](https://www.virustotal.com/gui/file/0ad2f4cd9f466baba73c699a55a1ff5d51211e371082df7a792b9f622a074b4b) |
| `BotLegger_0.17.0_windows_x86_64_setup.exe` | `d16658cee105884f852fbb63a48a988f9fd9128bc43a2d3e485651c5c81bcc68` | unsigned (SmartScreen warns on first launch) | BotLegger_0.17.0_windows_x86_64_setup.exe: ASLR, DEP | [0 of 67 engines flag it](https://www.virustotal.com/gui/file/d16658cee105884f852fbb63a48a988f9fd9128bc43a2d3e485651c5c81bcc68) |
| `bot-linux-x86_64.tar.gz` | `f4757eacf250c341d96a0f83366829e00078293d64cf965ea465787e9f5c4ca7` | unsigned archive; verify the SHA-256 in sha256.sum | bot: PIE, NX, full RELRO, stack canary | [0 of 60 engines flag it](https://www.virustotal.com/gui/file/f4757eacf250c341d96a0f83366829e00078293d64cf965ea465787e9f5c4ca7) |
| `bot-tui-aarch64-apple-darwin.tar.xz` | `0d3cbf01fdeeb5089916f08e7628047273cb386d991dcd696e03df7638a7ac2a` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 60 engines flag it](https://www.virustotal.com/gui/file/0d3cbf01fdeeb5089916f08e7628047273cb386d991dcd696e03df7638a7ac2a) |
| `bot-tui-x86_64-apple-darwin.tar.xz` | `3641018fa6d439927f9d576998b404858a6aeeccf0ed134918d156e5f33300a5` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/3641018fa6d439927f9d576998b404858a6aeeccf0ed134918d156e5f33300a5) |
| `bot-tui-x86_64-pc-windows-msvc.zip` | `cd61df3d08369b011c3b0dd7b2e655042e2784ff928e974ea1eb62184b4accaf` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP | [0 of 63 engines flag it](https://www.virustotal.com/gui/file/cd61df3d08369b011c3b0dd7b2e655042e2784ff928e974ea1eb62184b4accaf) |
| `bot-tui-x86_64-unknown-linux-gnu.tar.xz` | `fae51c1712e9e40741f5b4824d00e7d945904416da7a42eac0af89fdd9757565` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO, stack canary | [0 of 59 engines flag it](https://www.virustotal.com/gui/file/fae51c1712e9e40741f5b4824d00e7d945904416da7a42eac0af89fdd9757565) |
| `ggml-small-q5_1.bin` | `ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb` | data file, not a program; the apps accept only this SHA-256 | not applicable | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb) |

## Command-line installer scripts

Text scripts that download the command-line archives above and check their SHA-256. They are made from the previous release's scripts, and the release tooling refuses any change other than the version, download address, and checksum lines.

| File | SHA-256 |
|------|---------|
| `bot-tui-installer.ps1` | `7dc27660426e504a1ff881f14b0fb3ea00dc8eadc848864d847c26135f6e74a4` |
| `bot-tui-installer.sh` | `7d9e1ea6e00ca724d80bd81c8a0cb2f36cd186718b135e290131663a0fae5efb` |

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
