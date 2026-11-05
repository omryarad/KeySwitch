# Changelog

## KeySwitch Beta 2.1 (0.2.1, build 19)

Tag `v0.2.1-beta`.

- **Optional usage statistics, off by default.** *Settings → Share usage statistics*, after a screen that explains exactly what is sent. Only daily counts: conversions that succeeded, were not confirmed or failed, the failure reason from a fixed list, direction, replacement method, coarse duration, the kind of app (for example a browser), and versions. Never text, clipboard content, app or window names, or URLs. *What Is Sent…* shows the pending data. Turning it off deletes the random ID and the data on your Mac and on the server. Details: [PRIVACY.md](PRIVACY.md#usage-statistics-optional-off-by-default).
- Conversion, the shortcut, settings and automatic updates are unchanged. Updating from Beta 2.0 is automatic.

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
