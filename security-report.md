# BotLegger 0.10.0 security report

**All 10 checks passed.** 24 known exceptions were reviewed and kept (5 low risk, 19 no risk); they are listed at the end.

Built from commit `ecf2af4ec512` on 2026-11-15. Every check ran on the release's own commit and files, and the release is not published unless all of them pass.

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
| `BotLegger_0.10.0_linux_x86_64.tar.gz` | `f38fc7ebfc5eaaffbaa77e460193325d379677edcf3424010fa746dbff22d831` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO; 11 bundled libraries and helpers also checked | [0 of 74 engines flag it](https://www.virustotal.com/gui/file/f38fc7ebfc5eaaffbaa77e460193325d379677edcf3424010fa746dbff22d831) |
| `BotLegger_0.10.0_universal.dmg` | `43e17add9d6d77f6390875f25d4ade85e0ab1d5dbfe44081d7239e817736808d` | Developer ID (team 5S6TA8TSAC), notarized by Apple, ticket stapled, hardened runtime | PIE, stack canary | [0 of 74 engines flag it](https://www.virustotal.com/gui/file/43e17add9d6d77f6390875f25d4ade85e0ab1d5dbfe44081d7239e817736808d) |
| `BotLegger_0.10.0_windows_x86_64.zip` | `a3ef252447d6bd5df4f4688c34818e790aa0b902b76080b7621feeddd9baa16f` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP; 15 bundled libraries and helpers also checked | [0 of 74 engines flag it](https://www.virustotal.com/gui/file/a3ef252447d6bd5df4f4688c34818e790aa0b902b76080b7621feeddd9baa16f) |
| `BotLegger_0.10.0_windows_x86_64_setup.exe` | `d4abe6298e155928d43e311f471f184992e799445be28506475b38859f07e1f6` | unsigned (SmartScreen warns on first launch) | BotLegger_0.10.0_windows_x86_64_setup.exe: ASLR, DEP | [0 of 74 engines flag it](https://www.virustotal.com/gui/file/d4abe6298e155928d43e311f471f184992e799445be28506475b38859f07e1f6) |
| `bot-linux-x86_64.tar.gz` | `2e1e1f0806d4bb401ece60ee3d5d8766fa4c26c68d80518ee926f5069a1f76f7` | unsigned archive; verify the SHA-256 in sha256.sum | bot: PIE, NX, full RELRO, stack canary | [0 of 74 engines flag it](https://www.virustotal.com/gui/file/2e1e1f0806d4bb401ece60ee3d5d8766fa4c26c68d80518ee926f5069a1f76f7) |
| `bot-tui-aarch64-apple-darwin.tar.xz` | `da0f22a81bc49b0e7717956a21cf38f3958595010fe7a42eb8fe3b2ded2a719a` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 74 engines flag it](https://www.virustotal.com/gui/file/da0f22a81bc49b0e7717956a21cf38f3958595010fe7a42eb8fe3b2ded2a719a) |
| `bot-tui-x86_64-apple-darwin.tar.xz` | `534f7148af590489609d08648f003f81279206738f00e89baa67494d00ba135f` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 74 engines flag it](https://www.virustotal.com/gui/file/534f7148af590489609d08648f003f81279206738f00e89baa67494d00ba135f) |
| `bot-tui-x86_64-pc-windows-msvc.zip` | `85f926b5991c3907cacb70da65a95564f300d7cdf16dfd4d35175d7b9a01020b` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP | [0 of 74 engines flag it](https://www.virustotal.com/gui/file/85f926b5991c3907cacb70da65a95564f300d7cdf16dfd4d35175d7b9a01020b) |
| `bot-tui-x86_64-unknown-linux-gnu.tar.xz` | `7161baf1048cd996212cf641e89a78d2bf6bab86041528db84f7f7d8de8cf5d0` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO, stack canary | [0 of 74 engines flag it](https://www.virustotal.com/gui/file/7161baf1048cd996212cf641e89a78d2bf6bab86041528db84f7f7d8de8cf5d0) |
| `ggml-small-q5_1.bin` | `ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb` | data file, not a program; the apps accept only this SHA-256 | not applicable | [0 of 75 engines flag it](https://www.virustotal.com/gui/file/ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb) |

## Command-line installer scripts

Text scripts that download the command-line archives above and check their SHA-256. They are made from the previous release's scripts, and the release tooling refuses any change other than the version, download address, and checksum lines.

| File | SHA-256 |
|------|---------|
| `bot-tui-installer.ps1` | `8f2be3d5f9e813780bb33cadfa2c508e524d236cef406ec4efff2ac68141be83` |
| `bot-tui-installer.sh` | `9ef6bf8af0782f2a0b8a79f7f00e6469aa208a3c4e8722dc47cdbaa1d0d1d249` |

## Known exceptions

Scanners flag patterns, and some of what they flag is harmless, such as made-up credentials that tests use to check secrets are hidden. 24 known exceptions were reviewed and kept (5 low risk, 19 no risk). Each is looked at again by its review date, and nothing above medium risk is ever accepted: anything riskier is fixed. Components are described rather than named, so this list is not a map of what to attack.

| Kind | Risk | Count | Why it is kept | Review by |
|------|------|-------|----------------|-----------|
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
