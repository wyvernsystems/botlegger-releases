# BotLegger 0.13.0 security report

**All 10 checks passed.** 26 known exceptions were reviewed and kept (7 low risk, 19 no risk); they are listed at the end.

Built from commit `c78f27d8ef37` on 2026-11-18. Every check ran on the release's own commit and files, and the release is not published unless all of them pass.

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
| `BotLegger_0.13.0_linux_x86_64.tar.gz` | `d78af50a41bad3cb6fb78d8f377c13a18767bc2870f5d4171bc43aaa122f8967` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO; 11 bundled libraries and helpers also checked | [0 of 62 engines flag it](https://www.virustotal.com/gui/file/d78af50a41bad3cb6fb78d8f377c13a18767bc2870f5d4171bc43aaa122f8967) |
| `BotLegger_0.13.0_universal.dmg` | `517381ebb8c494c4b2e7e9496c69c8e18754b0233d4e66e115d610be4d525228` | Developer ID (team 5S6TA8TSAC), notarized by Apple, ticket stapled, hardened runtime | PIE, stack canary | [0 of 60 engines flag it](https://www.virustotal.com/gui/file/517381ebb8c494c4b2e7e9496c69c8e18754b0233d4e66e115d610be4d525228) |
| `BotLegger_0.13.0_windows_x86_64.zip` | `18af5221937cd3276ad2c651fcfc684e7d2de063a285481e2e37db268a84aab7` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP; 15 bundled libraries and helpers also checked | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/18af5221937cd3276ad2c651fcfc684e7d2de063a285481e2e37db268a84aab7) |
| `BotLegger_0.13.0_windows_x86_64_setup.exe` | `bbd56740c939425cec6897bef90959e4be33a4e585078305ba52f810f1424ba0` | unsigned (SmartScreen warns on first launch) | BotLegger_0.13.0_windows_x86_64_setup.exe: ASLR, DEP | [0 of 68 engines flag it](https://www.virustotal.com/gui/file/bbd56740c939425cec6897bef90959e4be33a4e585078305ba52f810f1424ba0) |
| `bot-linux-x86_64.tar.gz` | `52647991457557e6eccbe5216d83ef085d2e48d4d811ada492c7d6de556d0efe` | unsigned archive; verify the SHA-256 in sha256.sum | bot: PIE, NX, full RELRO, stack canary | [0 of 59 engines flag it](https://www.virustotal.com/gui/file/52647991457557e6eccbe5216d83ef085d2e48d4d811ada492c7d6de556d0efe) |
| `bot-tui-aarch64-apple-darwin.tar.xz` | `d7f014dac5d91efdc461dec33d0d0d7cccfb694e5866ce7f7c3476005b7c2a1f` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/d7f014dac5d91efdc461dec33d0d0d7cccfb694e5866ce7f7c3476005b7c2a1f) |
| `bot-tui-x86_64-apple-darwin.tar.xz` | `fc89b575f64506d705b7c85e52c4b03ddeff983c68941810c3aa3eae22a6c8a8` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/fc89b575f64506d705b7c85e52c4b03ddeff983c68941810c3aa3eae22a6c8a8) |
| `bot-tui-x86_64-pc-windows-msvc.zip` | `fa1ff841ddbb42370e4809eda55ed14bc5ae8e7b8c0133a895249ea1593ebbef` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP | [0 of 64 engines flag it](https://www.virustotal.com/gui/file/fa1ff841ddbb42370e4809eda55ed14bc5ae8e7b8c0133a895249ea1593ebbef) |
| `bot-tui-x86_64-unknown-linux-gnu.tar.xz` | `877cd981b405074671abb9c80b85543d3c6192248692a4a838b388340eeb22f9` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO, stack canary | [0 of 58 engines flag it](https://www.virustotal.com/gui/file/877cd981b405074671abb9c80b85543d3c6192248692a4a838b388340eeb22f9) |
| `ggml-small-q5_1.bin` | `ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb` | data file, not a program; the apps accept only this SHA-256 | not applicable | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb) |

## Command-line installer scripts

Text scripts that download the command-line archives above and check their SHA-256. They are made from the previous release's scripts, and the release tooling refuses any change other than the version, download address, and checksum lines.

| File | SHA-256 |
|------|---------|
| `bot-tui-installer.ps1` | `4185289a43e014e302c70a3fdf8dc25677ad9d67b03f150a6693a474ab0e9f46` |
| `bot-tui-installer.sh` | `36ebd38e4a13c217db201a41ec88049da5328d5d8cdb5197e50bfe6b672ded35` |

## Known exceptions

Scanners flag patterns, and some of what they flag is harmless, such as made-up credentials that tests use to check secrets are hidden. 26 known exceptions were reviewed and kept (7 low risk, 19 no risk). Each is looked at again by its review date, and nothing above medium risk is ever accepted: anything riskier is fixed. Components are described rather than named, so this list is not a map of what to attack.

| Kind | Risk | Count | Why it is kept | Review by |
|------|------|-------|----------------|-----------|
| Third-party code | low | 2 | A widely used third-party library whose maintainers stopped maintaining it. It has no known vulnerability; we are planning its replacement and review this again within three months. | 2027-02-16 |
| Build workflow | low | 1 | A build step runs a programming toolchain's official installer, downloaded over an encrypted connection, and only when the toolchain is missing. The risk rests on that vendor's own download site; changing it would break the release build. | 2027-11-07 |
| Build workflow | low | 1 | A build step writes fixed values and the build machine's own install paths into the build environment; no outside input reaches it. | 2027-11-07 |
| Build workflow | low | 1 | Build commands are inserted from the release tool's own configuration in the repository, never from outside input such as issue or pull request text. | 2027-11-07 |
| Build workflow | low | 1 | The build machine image is chosen and pinned by the release tool's own plan in the repository; the workflow only passes that choice along. | 2027-11-07 |
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
