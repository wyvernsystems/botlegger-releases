# BotLegger 0.21.0 security report

**All 10 checks passed.** 25 known exceptions were reviewed and kept (6 low risk, 19 no risk); they are listed at the end.

Built from commit `ca026131ecf1` on 2026-11-25. Every check ran on the release's own commit and files, and the release is not published unless all of them pass.

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
| `BotLegger_0.21.0_linux_x86_64.tar.gz` | `efa4f4b44d6d8a004ca96824a31af0bd2a409e9d1bcaaaa1915ab659ca50ada5` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO; 11 bundled libraries and helpers also checked | [0 of 62 engines flag it](https://www.virustotal.com/gui/file/efa4f4b44d6d8a004ca96824a31af0bd2a409e9d1bcaaaa1915ab659ca50ada5) |
| `BotLegger_0.21.0_universal.dmg` | `eacb38abdabfa7cafcd4f239828623d1ae73c9a1ee63a69a7d0daa5c67dc1d22` | Developer ID (team 5S6TA8TSAC), notarized by Apple, ticket stapled, hardened runtime | PIE, stack canary | [0 of 58 engines flag it](https://www.virustotal.com/gui/file/eacb38abdabfa7cafcd4f239828623d1ae73c9a1ee63a69a7d0daa5c67dc1d22) |
| `BotLegger_0.21.0_windows_x86_64.zip` | `2fe93ef5405c2caa465e6f5c67cc5339fd4fe2caed2794bfe106e05e5e8e174c` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP; 15 bundled libraries and helpers also checked | [0 of 60 engines flag it](https://www.virustotal.com/gui/file/2fe93ef5405c2caa465e6f5c67cc5339fd4fe2caed2794bfe106e05e5e8e174c) |
| `BotLegger_0.21.0_windows_x86_64_setup.exe` | `dc39d04c91c17ba8e677892d1e12dd10c2c925d356b417a05b893b0828bc5150` | unsigned (SmartScreen warns on first launch) | BotLegger_0.21.0_windows_x86_64_setup.exe: ASLR, DEP | [0 of 68 engines flag it](https://www.virustotal.com/gui/file/dc39d04c91c17ba8e677892d1e12dd10c2c925d356b417a05b893b0828bc5150) |
| `bot-linux-x86_64.tar.gz` | `438a4a2d7fcbb648a2de36c47031528abd6654c0d34bacd8ba6ac02c81c2cf67` | unsigned archive; verify the SHA-256 in sha256.sum | bot: PIE, NX, full RELRO, stack canary | [0 of 59 engines flag it](https://www.virustotal.com/gui/file/438a4a2d7fcbb648a2de36c47031528abd6654c0d34bacd8ba6ac02c81c2cf67) |
| `bot-tui-aarch64-apple-darwin.tar.xz` | `7c180b2b94e174bc97237cd8594462ae3df85153c830ada4ec3905f55a977083` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/7c180b2b94e174bc97237cd8594462ae3df85153c830ada4ec3905f55a977083) |
| `bot-tui-x86_64-apple-darwin.tar.xz` | `18fa5f207e6df2da469ca4e699ee51a4a29dc439101a89d2dab8d3e3624a2eb0` | Developer ID (team 5S6TA8TSAC), hardened runtime | PIE, stack canary | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/18fa5f207e6df2da469ca4e699ee51a4a29dc439101a89d2dab8d3e3624a2eb0) |
| `bot-tui-x86_64-pc-windows-msvc.zip` | `3c4e3542566f9a5a652fad3c48a1ff7bbab039b8bfd8c35d435b9c9c51488288` | unsigned (SmartScreen warns on first launch) | botlegger.exe: ASLR, high-entropy ASLR, DEP | [0 of 64 engines flag it](https://www.virustotal.com/gui/file/3c4e3542566f9a5a652fad3c48a1ff7bbab039b8bfd8c35d435b9c9c51488288) |
| `bot-tui-x86_64-unknown-linux-gnu.tar.xz` | `540353abf36b741c0214debe1270ffca57b2d3899471722c942c4e10ade0c056` | unsigned archive; verify the SHA-256 in sha256.sum | botlegger: PIE, NX, full RELRO, stack canary | [0 of 60 engines flag it](https://www.virustotal.com/gui/file/540353abf36b741c0214debe1270ffca57b2d3899471722c942c4e10ade0c056) |
| `ggml-small-q5_1.bin` | `ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb` | data file, not a program; the apps accept only this SHA-256 | not applicable | [0 of 61 engines flag it](https://www.virustotal.com/gui/file/ae85e4a935d7a567bd102fe55afc16bb595bdb618e11b2fc7591bc08120411bb) |

## Command-line installer scripts

Text scripts that download the command-line archives above and check their SHA-256. They are made from the previous release's scripts, and the release tooling refuses any change other than the version, download address, and checksum lines.

| File | SHA-256 |
|------|---------|
| `bot-tui-installer.ps1` | `3f0c567df72856c08f2d11e0ddc4ddf2525280b4d743172995b8695fe60f36f2` |
| `bot-tui-installer.sh` | `4b5ec7d38da4f0cb15a295f1a0449160c540f4e624b15f81b87e4e1f5e8f20f9` |

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
