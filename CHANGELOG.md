# Changelog

## KeySwitch Beta 2.1 (0.2.1, build 19)

Tag `v0.2.1-beta`.

- **Usage statistics are now part of using KeySwitch.** At first launch, and once after updating from Beta 2.0, a short consent screen links to the [Terms of Use](TERMS.md) and the Privacy Policy, which describe what is sent: daily counts of conversions that succeeded, were not confirmed or failed, the failure reason from a fixed list, direction, replacement method, coarse duration, the kind of app (for example a browser), versions, and a random installation ID. Never text, clipboard content, URLs, window titles or document content. Choose *Agree and Continue* or *Quit KeySwitch*; nothing is collected before you agree, and the shortcut stays off if you do not. *Settings → Privacy* shows the full statement, *What Is Sent…* and *Delete Statistics and Quit…*, which deletes the data on your Mac and on the server. Details: [PRIVACY.md](PRIVACY.md#usage-statistics-a-condition-of-use).
- After a conversion the cursor sits right after the converted text, and the keyboard input language switches to match the conversion. The switch can be turned off in *Settings → Automatically switch keyboard language* (on by default).
- The shortcut and settings are otherwise unchanged. Updating from Beta 2.0 is automatic; the statistics screen appears on the first launch after the update.

## KeySwitch Beta 2.0 (0.2.0, build 18)

First public beta. Tag `v0.2.0-beta.2`.

- **Automatic updates** (Sparkle): a daily check on GitHub, background download, installed when you quit. *Check for Updates…* and *Update Automatically* in the menu bar menu. Every update is checked against KeySwitch's EdDSA signature and Apple's code signature before it is installed. Settings, history and Accessibility permission are kept.
- Refined icons: "T" next to "א" in the app icon; lighter arrows and a clearer dashed line in the menu bar icon.
- Privacy statement updated for the update check ([PRIVACY.md](PRIVACY.md)).

Everything from 0.2.0 beta 1:

- Converts selected text between Hebrew and English keyboard layouts, in place, with one global shortcut (⇧⌘J by default).
- Bilingual (Hebrew/English) welcome guide: what KeySwitch does, Accessibility permission, shortcut, practice field. Reopen it any time from Settings.
- Menu bar–only app with a new ⇄ menu bar icon (template, light and dark), no Dock icon. Optional start at login.
- Optional local conversion history, off by default.
- In-memory diagnostics with no text content, copied only on request.
- Universal app (Apple Silicon and Intel), macOS 13 or later.

**Known limitations:** replacement is not yet fully reliable in some web page text fields in Chrome (for example the Google and YouTube search boxes; the address bar works). Upgrading from a pre-release build (0.1.x) requires granting Accessibility permission once more, because the app is now signed with a Developer ID.

## 0.2.0 beta 1 (build 17)

Release candidate, notarized but not published.
