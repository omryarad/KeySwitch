# Security

KeySwitch has Accessibility access to the apps you type in, so we take security reports seriously.

## Reporting a vulnerability

Please **do not** open a public issue for security problems. Use GitHub's private reporting instead: **Security → Report a vulnerability** in this repository.

Include the KeySwitch version (Settings → About), your macOS version, and steps to reproduce. We aim to acknowledge reports within a few days.

## Verifying a download

- Download KeySwitch only from this repository's **Releases** page.
- Each release lists SHA-256 checksums in `SHA256SUMS.txt`.
- Official releases are signed with an Apple Developer ID and notarized by Apple. To check an installed copy:
  ```bash
  spctl -a -vv /Applications/KeySwitch.app
  codesign -dv --verbose=2 /Applications/KeySwitch.app
  ```
  `spctl` should report `accepted` and `source=Notarized Developer ID`.

**Never** follow instructions, from anyone, that tell you to remove macOS quarantine (`xattr -d com.apple.quarantine`) from a copy of KeySwitch.
