# BotLegger 0.9.0 security report

**All 10 checks passed.** 25 known exceptions were reviewed and kept (6 low risk, 19 no risk); they are listed at the end.

Built from commit `40e39eb5d119` on 2026-11-15. Every check ran on the release's own commit and files, and the release is not published unless all of them pass.

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
| `BotLegger_0.9.0_linux_x86_64.tar.gz` | `78ec4585872dcf02dcf760f11e7704dda65fd97a22c1c847da0da9ccaa7cc90b` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO; 11 bundled libraries and helpers also checked | [0 of 52 engines flag it](https://www.virustotal.com/gui/file/78ec4585872dcf02dcf760f11e7704dda65fd97a22c1c847da0da9ccaa7cc90b) |
| `BotLegger_0.9.0_universal.dmg` | `1c8ca8bb42ef485de2a3948ac9ff8209f87eb8b94a1fdd48934c70ea255f1ca1` | Developer ID (team 5S6TA8TSAC), notarized by Apple, ticket stapled, hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/1c8ca8bb42ef485de2a3948ac9ff8209f87eb8b94a1fdd48934c70ea255f1ca1) |
| `BotLegger_0.9.0_windows_x86_64.zip` | `f871f60b390ebad1df8f7d93f5c89d45707685fb063403aa1f6d6583cf85a790` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP; 15 bundled libraries and helpers also checked | [0 of 65 engines flag it](https://www.virustotal.com/gui/file/f871f60b390ebad1df8f7d93f5c89d45707685fb063403aa1f6d6583cf85a790) |
| `BotLegger_0.9.0_windows_x86_64_setup.exe` | `e61642be9e28776d5381fae03cc38d769738145ae96973fa0dfe495bc9abe5cf` | unsigned (SmartScreen warns on first launch) | BotLegger_0.9.0_windows_x86_64_setup.exe: ASLR, DEP | [0 of 69 engines flag it](https://www.virustotal.com/gui/file/e61642be9e28776d5381fae03cc38d769738145ae96973fa0dfe495bc9abe5cf) |
| `bot-linux-x86_64.tar.gz` | `8ff8656c00801d7d4963b001a3428c39a5df11f65e01476c9cef350af44e210c` | unsigned archive; verify the SHA-256 in sha256.sum | bot: PIE, NX, full RELRO, stack canary | [0 of 60 engines flag it](https://www.virustotal.com/gui/file/8ff8656c00801d7d4963b001a3428c39a5df11f65e01476c9cef350af44e210c) |
| `bot-tui-aarch64-apple-darwin.tar.xz` | `cf6f5ec572c0689ab908b92cefa8c05740d49c0b485ec75399c731b9093e7655` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/cf6f5ec572c0689ab908b92cefa8c05740d49c0b485ec75399c731b9093e7655) |
| `bot-tui-x86_64-apple-darwin.tar.xz` | `34f8b10fbb940d4407ea9fd1dc4a8a52b5104f6cddf93ddbb661fd2dfeae568f` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 37 engines flag it](https://www.virustotal.com/gui/file/34f8b10fbb940d4407ea9fd1dc4a8a52b5104f6cddf93ddbb661fd2dfeae568f) |
| `bot-tui-x86_64-pc-windows-msvc.zip` | `a940334edbeb7fdfcbe4554a2c3dae00274c1cd288baf5e271f8aed4844f5367` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP | [0 of 65 engines flag it](https://www.virustotal.com/gui/file/a940334edbeb7fdfcbe4554a2c3dae00274c1cd288baf5e271f8aed4844f5367) |
| `bot-tui-x86_64-unknown-linux-gnu.tar.xz` | `ca28cb083448f98392765e3cefdee0e02ad6ee4e9e21cee918b213cf9c8d6452` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO, stack canary | [0 of 60 engines flag it](https://www.virustotal.com/gui/file/ca28cb083448f98392765e3cefdee0e02ad6ee4e9e21cee918b213cf9c8d6452) |
| `ggml-small-q5_1.bin` | `ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb` | data file, not a program; the apps accept only this SHA-256 | not applicable | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb) |

## Command-line installer scripts

Text scripts that download the command-line archives above and check their SHA-256. They are made from the previous release's scripts, and the release tooling refuses any change other than the version, download address, and checksum lines.

| File | SHA-256 |
|------|---------|
| `bot-tui-installer.ps1` | `83fe02b6b7b6d94826249439eec2cc877ab7f9982fa17ecb120e4d02f5064e20` |
| `bot-tui-installer.sh` | `5e606bd82e1245b420ff6182b08e98b91ccbdc2426a3b313c94344a2ffef9687` |

## Known exceptions

Scanners flag patterns, and some of what they flag is harmless, such as made-up credentials that tests use to check secrets are hidden. 25 known exceptions were reviewed and kept (6 low risk, 19 no risk). Each is looked at again by its review date, and nothing above medium risk is ever accepted: anything riskier is fixed. Components are described rather than named, so this list is not a map of what to attack.

| Kind | Risk | Count | Why it is kept | Review by |
|------|------|-------|----------------|-----------|
| Build workflow | low | 1 | A build step runs a programming toolchain's official installer, downloaded over an encrypted connection, and only when the toolchain is missing. The risk rests on that vendor's own download site; changing it would break the release build. | 2027-11-07 |
| Build workflow | low | 1 | A build step writes fixed values and the build machine's own install paths into the build environment; no outside input reaches it. | 2027-11-07 |
| Build workflow | low | 1 | Build commands are inserted from the release tool's own configuration in the repository, never from outside input such as issue or pull request text. | 2027-11-07 |
| Build workflow | low | 1 | The build machine image is chosen and pinned by the release tool's own plan in the repository; the workflow only passes that choice along. | 2027-11-07 |
| Third-party licence | low | 1 | A third-party library under a licence outside our default list. We use it unmodified and ship its notice, which is all that licence asks; replacing it would break a feature. | 2027-11-07 |
| Third-party licence | low | 1 | Third-party map data under an attribution licence. We ship it unmodified with the required attribution; the code that reads it is under a permissive licence. Replacing it would break a feature. | 2027-11-07 |
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
