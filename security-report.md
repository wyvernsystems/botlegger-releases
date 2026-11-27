# BotLegger 0.23.0 security report

**All 10 checks passed.** 25 known exceptions were reviewed and kept (6 low risk, 19 no risk); they are listed at the end.

Built from commit `aa00f2d24d40` on 2026-11-26. Every check ran on the release's own commit and files, and the release is not published unless all of them pass.

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
| `BotLegger_0.23.0_linux_x86_64.tar.gz` | `d27a05f9987330860e5156fe5c5c92f4f22ba745e1c3c742e9ae1214a258dda2` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO; 11 bundled libraries and helpers also checked | [0 of 62 engines flag it](https://www.virustotal.com/gui/file/d27a05f9987330860e5156fe5c5c92f4f22ba745e1c3c742e9ae1214a258dda2) |
| `BotLegger_0.23.0_universal.dmg` | `6d081739582f0c0250f1721f65e5aba8e8ddd189cb7056d128e8986a9129bbe1` | Developer ID (team 5S6TA8TSAC), notarized by Apple, ticket stapled, hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/6d081739582f0c0250f1721f65e5aba8e8ddd189cb7056d128e8986a9129bbe1) |
| `BotLegger_0.23.0_windows_x86_64.zip` | `22e60375365288a9a2162c86e5632555b406863fadff3afe88dda99a1d1cd882` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP; 15 bundled libraries and helpers also checked | [0 of 66 engines flag it](https://www.virustotal.com/gui/file/22e60375365288a9a2162c86e5632555b406863fadff3afe88dda99a1d1cd882) |
| `BotLegger_0.23.0_windows_x86_64_setup.exe` | `d5f71803b3013fa1487e6a75047f153d0d8fafb82507939aca9ed51cd1fffdd2` | unsigned (SmartScreen warns on first launch) | BotLegger_0.23.0_windows_x86_64_setup.exe: ASLR, DEP | [0 of 68 engines flag it](https://www.virustotal.com/gui/file/d5f71803b3013fa1487e6a75047f153d0d8fafb82507939aca9ed51cd1fffdd2) |
| `bot-linux-x86_64.tar.gz` | `f90ce920bddd16af9ffc1cfdb6a5a07e861abd7f9dc09c8b0f025cbaba5a2d0a` | unsigned archive; verify the SHA-256 in sha256.sum | bot: PIE, NX, full RELRO, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/f90ce920bddd16af9ffc1cfdb6a5a07e861abd7f9dc09c8b0f025cbaba5a2d0a) |
| `bot-tui-aarch64-apple-darwin.tar.xz` | `6b3fa24f4cb6a15f86c423c52fd1aaf4c5595a88821a6249f2294dbf0c7ad684` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/6b3fa24f4cb6a15f86c423c52fd1aaf4c5595a88821a6249f2294dbf0c7ad684) |
| `bot-tui-x86_64-apple-darwin.tar.xz` | `74492e86afafab199b238b450525e671a2f9a409d377559b179532d50aedb108` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/74492e86afafab199b238b450525e671a2f9a409d377559b179532d50aedb108) |
| `bot-tui-x86_64-pc-windows-msvc.zip` | `9843dc3fcc5d0afe842d1507d0d2c6a687b4a12c9ba81e2b00dc39a617bc9a1c` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP | [0 of 64 engines flag it](https://www.virustotal.com/gui/file/9843dc3fcc5d0afe842d1507d0d2c6a687b4a12c9ba81e2b00dc39a617bc9a1c) |
| `bot-tui-x86_64-unknown-linux-gnu.tar.xz` | `f2d12762e7fd9fc4d831f591e860bdbde472093b75bce148651918336b23465c` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO, stack canary | [0 of 60 engines flag it](https://www.virustotal.com/gui/file/f2d12762e7fd9fc4d831f591e860bdbde472093b75bce148651918336b23465c) |
| `ggml-small-q5_1.bin` | `ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb` | data file, not a program; the apps accept only this SHA-256 | not applicable | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb) |

## Command-line installer scripts

Text scripts that download the command-line archives above and check their SHA-256. They are made from the previous release's scripts, and the release tooling refuses any change other than the version, download address, and checksum lines.

| File | SHA-256 |
|------|---------|
| `bot-tui-installer.ps1` | `ad6427b348650bd7ba72f741c66c55763696a2607c3d49e49da23361dda6ea0e` |
| `bot-tui-installer.sh` | `0afaf5ec822713477e982b8fe1b94fd4bb8b0beec98bb5382a4844804e3d723c` |

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
