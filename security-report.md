# BotLegger 0.11.1 security report

**All 10 checks passed.** 24 known exceptions were reviewed and kept (5 low risk, 19 no risk); they are listed at the end.

Built from commit `49184dd54adb` on 2026-11-16. Every check ran on the release's own commit and files, and the release is not published unless all of them pass.

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
| `BotLegger_0.11.1_linux_x86_64.tar.gz` | `a5e94fdfd3f3f00e7c4470e82666cc48ec57b9c593c07df6a3d513945d02a741` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO; 11 bundled libraries and helpers also checked | [0 of 74 engines flag it](https://www.virustotal.com/gui/file/a5e94fdfd3f3f00e7c4470e82666cc48ec57b9c593c07df6a3d513945d02a741) |
| `BotLegger_0.11.1_universal.dmg` | `fa41b9c0e17a002d67d10dd51f89946394ae374359c56fc38a42d1771507d6a8` | Developer ID (team 5S6TA8TSAC), notarized by Apple, ticket stapled, hardened runtime | PIE, stack canary | [0 of 73 engines flag it](https://www.virustotal.com/gui/file/fa41b9c0e17a002d67d10dd51f89946394ae374359c56fc38a42d1771507d6a8) |
| `BotLegger_0.11.1_windows_x86_64.zip` | `184d53c1a6323b990cc25ea339dcff43d171ff9e39a187c62288a51bfba6257f` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP; 15 bundled libraries and helpers also checked | [0 of 73 engines flag it](https://www.virustotal.com/gui/file/184d53c1a6323b990cc25ea339dcff43d171ff9e39a187c62288a51bfba6257f) |
| `BotLegger_0.11.1_windows_x86_64_setup.exe` | `70a634c5aa9520c7c78fa9a6dda5c8a476f95bec830b9ed7d69eddfc87706d2d` | unsigned (SmartScreen warns on first launch) | BotLegger_0.11.1_windows_x86_64_setup.exe: ASLR, DEP | [0 of 74 engines flag it](https://www.virustotal.com/gui/file/70a634c5aa9520c7c78fa9a6dda5c8a476f95bec830b9ed7d69eddfc87706d2d) |
| `bot-linux-x86_64.tar.gz` | `8a8fbdb7c7c4d13fe7876495673889741b5914b83f0b43e3d75d477ef4577ef2` | unsigned archive; verify the SHA-256 in sha256.sum | bot: PIE, NX, full RELRO, stack canary | [0 of 73 engines flag it](https://www.virustotal.com/gui/file/8a8fbdb7c7c4d13fe7876495673889741b5914b83f0b43e3d75d477ef4577ef2) |
| `bot-tui-aarch64-apple-darwin.tar.xz` | `5ed17b8e9ea5c03d0ea3af6d302cd8bb1f1d58a3a6deb22c3996dd4f49a5fd2e` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 73 engines flag it](https://www.virustotal.com/gui/file/5ed17b8e9ea5c03d0ea3af6d302cd8bb1f1d58a3a6deb22c3996dd4f49a5fd2e) |
| `bot-tui-x86_64-apple-darwin.tar.xz` | `80215b5ccf8b763b2b50a2dbef31bd48aeb16df8d00ae54c38634657da8bd9e4` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 74 engines flag it](https://www.virustotal.com/gui/file/80215b5ccf8b763b2b50a2dbef31bd48aeb16df8d00ae54c38634657da8bd9e4) |
| `bot-tui-x86_64-pc-windows-msvc.zip` | `f26e07fe27163b43ea3bdae1a9be0240c0e9444c19011cbe8b647f2391a1a982` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP | [0 of 73 engines flag it](https://www.virustotal.com/gui/file/f26e07fe27163b43ea3bdae1a9be0240c0e9444c19011cbe8b647f2391a1a982) |
| `bot-tui-x86_64-unknown-linux-gnu.tar.xz` | `0ccc7f70d701ae2e5db9a344e5be3cc12c1330ae99a1deb32d9d9b7394676232` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO, stack canary | [0 of 73 engines flag it](https://www.virustotal.com/gui/file/0ccc7f70d701ae2e5db9a344e5be3cc12c1330ae99a1deb32d9d9b7394676232) |
| `ggml-small-q5_1.bin` | `ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb` | data file, not a program; the apps accept only this SHA-256 | not applicable | [0 of 75 engines flag it](https://www.virustotal.com/gui/file/ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb) |

## Command-line installer scripts

Text scripts that download the command-line archives above and check their SHA-256. They are made from the previous release's scripts, and the release tooling refuses any change other than the version, download address, and checksum lines.

| File | SHA-256 |
|------|---------|
| `bot-tui-installer.ps1` | `b16903d70365ca899999f72bd55aa18f16970d2f819de1f0e458d341a65ea516` |
| `bot-tui-installer.sh` | `ef7ce76b91e569f6fcaf31fd8a025233a4545125ddd1e78f34dbc8f9f1e1f151` |

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
