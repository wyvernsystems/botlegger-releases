# BotLegger 0.20.0 security report

**All 10 checks passed.** 25 known exceptions were reviewed and kept (6 low risk, 19 no risk); they are listed at the end.

Built from commit `49d00b1c5706` on 2026-11-24. Every check ran on the release's own commit and files, and the release is not published unless all of them pass.

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
| `BotLegger_0.20.0_linux_x86_64.tar.gz` | `083217b446520e1aa9f26d62da5dae1f158da230cfdf20ddcaba1d6ee8a2c006` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO; 11 bundled libraries and helpers also checked | [0 of 59 engines flag it](https://www.virustotal.com/gui/file/083217b446520e1aa9f26d62da5dae1f158da230cfdf20ddcaba1d6ee8a2c006) |
| `BotLegger_0.20.0_universal.dmg` | `0f9ef995bf3dd92c5dfb927a4bb3820518c211925c4773a1aab4cd4289b1eb7e` | Developer ID (team 5S6TA8TSAC), notarized by Apple, ticket stapled, hardened runtime | PIE, stack canary | [0 of 59 engines flag it](https://www.virustotal.com/gui/file/0f9ef995bf3dd92c5dfb927a4bb3820518c211925c4773a1aab4cd4289b1eb7e) |
| `BotLegger_0.20.0_windows_x86_64.zip` | `935e1c3a579fd3ad4717dba10c1304bdb86d7d71d5f92df3194f78cf6f2123e4` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP; 15 bundled libraries and helpers also checked | [0 of 65 engines flag it](https://www.virustotal.com/gui/file/935e1c3a579fd3ad4717dba10c1304bdb86d7d71d5f92df3194f78cf6f2123e4) |
| `BotLegger_0.20.0_windows_x86_64_setup.exe` | `2ab1e2b38bb3d0a7271eede33e7d52dcc6200f2c8396673b5c42817beef1f867` | unsigned (SmartScreen warns on first launch) | BotLegger_0.20.0_windows_x86_64_setup.exe: ASLR, DEP | [0 of 66 engines flag it](https://www.virustotal.com/gui/file/2ab1e2b38bb3d0a7271eede33e7d52dcc6200f2c8396673b5c42817beef1f867) |
| `bot-linux-x86_64.tar.gz` | `5e94d8c6da9e9f8c06b3becdaf7d330313252938927484dbf1f5baf64e337558` | unsigned archive; verify the SHA-256 in sha256.sum | bot: PIE, NX, full RELRO, stack canary | [0 of 59 engines flag it](https://www.virustotal.com/gui/file/5e94d8c6da9e9f8c06b3becdaf7d330313252938927484dbf1f5baf64e337558) |
| `bot-tui-aarch64-apple-darwin.tar.xz` | `51af854dbcb97753b7bb558480414cbcc721c9d73ee8cc090e9ef82c947944d6` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 58 engines flag it](https://www.virustotal.com/gui/file/51af854dbcb97753b7bb558480414cbcc721c9d73ee8cc090e9ef82c947944d6) |
| `bot-tui-x86_64-apple-darwin.tar.xz` | `e03478dc73eee9e762e40892bd53de4868c63486a36473828f0004be485caca8` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 58 engines flag it](https://www.virustotal.com/gui/file/e03478dc73eee9e762e40892bd53de4868c63486a36473828f0004be485caca8) |
| `bot-tui-x86_64-pc-windows-msvc.zip` | `0976bc6129ad1e7a3eed83504f092b398f3dae2e4891ab25d0f0d0a0e347f616` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP | [0 of 62 engines flag it](https://www.virustotal.com/gui/file/0976bc6129ad1e7a3eed83504f092b398f3dae2e4891ab25d0f0d0a0e347f616) |
| `bot-tui-x86_64-unknown-linux-gnu.tar.xz` | `ff39fb7cbd2c4217ed96e41f9e6f894db2e1df1e3a526f0d4c31e0eb8e80bf3c` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO, stack canary | [0 of 57 engines flag it](https://www.virustotal.com/gui/file/ff39fb7cbd2c4217ed96e41f9e6f894db2e1df1e3a526f0d4c31e0eb8e80bf3c) |
| `ggml-small-q5_1.bin` | `ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb` | data file, not a program; the apps accept only this SHA-256 | not applicable | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb) |

## Command-line installer scripts

Text scripts that download the command-line archives above and check their SHA-256. They are made from the previous release's scripts, and the release tooling refuses any change other than the version, download address, and checksum lines.

| File | SHA-256 |
|------|---------|
| `bot-tui-installer.ps1` | `7e802027ecdcc28ded3789e0e5147587124e278255d8a5afa0c48dd063277d1d` |
| `bot-tui-installer.sh` | `791930ca4d743b75973b455b6a74232227330b788ff1647d7c8e4dadec87005e` |

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
