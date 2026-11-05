# Privacy

**Short version:** KeySwitch works entirely on your Mac. Your text never leaves it. Its network requests are a daily check for updates on GitHub (you can turn it off) and, **only if you turn it on**, anonymous usage statistics. Conversion history is off unless you turn it on.

This statement describes KeySwitch from version 0.2.1 (build 19, the first version with optional usage statistics). Build 18 has the update check only; build 17 and earlier have no network code at all. It was written from a review of the app's source code, not as a marketing summary. If a future version changes any of this, this page will change with it.

## What KeySwitch accesses, and when

| What | When | Why |
|---|---|---|
| The selected text and the field's text in the active app (Accessibility) | Only after you press the KeySwitch shortcut | To read what you selected, convert it, and check afterwards that the replacement really happened. The text is held in memory only for that operation. |
| Keyboard events (Copy / Paste) sent to the active app | Only during a conversion, in apps that need it (mostly browsers) | Some apps only accept a replacement through their own Copy and Paste. |
| Your clipboard | Only during such a Copy/Paste conversion | KeySwitch saves your current clipboard in memory, uses the clipboard for about a second, then puts your content back. It only restores it if nothing else has changed the clipboard in the meantime. |

KeySwitch does **not**:
- access the network for anything except the update check and, if you turn them on, the usage statistics described below;
- include analytics SDKs, crash reporters, or third-party SDKs other than the Sparkle update framework. Usage statistics are sent by KeySwitch's own code;
- log or store your text, except in the optional history described below;
- work in password fields. Secure text fields are refused before anything is read;
- run when the clipboard holds content that password managers mark as private (concealed or transient). It leaves it untouched.

Temporary clipboard items are marked using the [nspasteboard.org](http://nspasteboard.org) conventions, so clipboard managers that honour them (for example Maccy) skip them.

## Update checks

KeySwitch uses [Sparkle](https://sparkle-project.org), an open-source update framework for Mac apps.

| What | Details |
|---|---|
| When | About once a day while KeySwitch is running, and when you choose *Check for Updates…* |
| Where | `raw.githubusercontent.com` (the list of versions) and `github.com` (the update itself, only when there is one). Both are GitHub, over HTTPS. |
| What is sent | A normal web request. It contains no identifier, no settings, nothing about your text or other apps. GitHub, like any web server, receives your IP address and a user agent with KeySwitch's and Sparkle's version numbers. GitHub's own privacy statement covers what it logs. |
| What is not sent | Sparkle's optional system profile (hardware, macOS version, language) is turned off. |
| Installing | A new version is downloaded in the background and installed when you quit KeySwitch. It is accepted only if it is signed by KeySwitch's developer: Sparkle checks the update's cryptographic (EdDSA) signature, the signature of the version list itself, and Apple's code signature. Your settings, history and Accessibility permission are kept. |
| Turning it off | Menu bar icon → *Update Automatically*. With it off, KeySwitch makes no update requests unless you choose *Check for Updates…*. |

The maintainer may look at GitHub's public download counters for each release (how many times a file was downloaded). These are totals kept by GitHub and are not linked to you.

## Usage statistics (optional, off by default)

From version 0.2.1, KeySwitch can share usage statistics, which help show whether it works and where it fails. **It is off unless you turn it on** in *Settings → Share usage statistics*, after a screen that explains what is sent. Nothing is sent, and no identifier exists, before you agree. *What Is Sent…* shows the exact data waiting to be sent.

| What | Details |
|---|---|
| What is sent | Daily counts of shortcut presses and of conversions that succeeded, were not confirmed, or failed. The failure reason, from a fixed list (for example "no selection", "the app did not accept the replacement"). The conversion direction (Hebrew→English or English→Hebrew). The replacement method. The duration in coarse buckets (for example 100–250 ms). The **kind** of app (browser, messaging, AI app, code editor, Apple app, other). The KeySwitch version and build, the macOS version (for example 15.1), the update channel, and the local date. |
| Identifier | A random ID created when you turn statistics on, used only to count active users and retention. It is not derived from your Mac, your account or anything else. On the server it is stored only as a keyed hash. Turning statistics off and on again creates a new, unrelated ID. |
| What is never sent | The text you select, convert or type. Clipboard content. App names or bundle identifiers. Window titles, document names or URLs. Your name, user name, computer name, email, hardware identifiers, language or time zone. |
| When | At most once an hour, in the background. Sending never delays or affects a conversion. If you are offline, up to 35 days are kept on your Mac (`~/Library/Application Support/org.keyswitch.KeySwitch/telemetry.json`, readable only by your account) and sent later. Older days are dropped. |
| Where | A server run by KeySwitch's developer on Cloudflare Workers, over HTTPS. Cloudflare processes your IP address to deliver the request. KeySwitch's server does not store IP addresses and keeps no request logs. Cloudflare's own privacy policy covers its processing. |
| Retention | Statistics are deleted after 400 days. |
| Turning it off, deleting your data | *Settings → Share usage statistics*. This immediately deletes the ID and the queued data on your Mac, and asks the server to delete everything stored for that ID. If your Mac is offline at that moment, KeySwitch repeats the request the next time it starts, until the server confirms it. |
| Who sees it | Only the developer, through a private dashboard behind sign-in. Statistics are not sold or shared. Aggregated totals (for example "N active users") may be published. |

## Data stored on your Mac

| Data | Where | Default |
|---|---|---|
| Settings: language, shortcut, options, whether the guide was completed | `~/Library/Preferences/org.keyswitch.KeySwitch.plist` | Always |
| **Conversion history**: original and converted text, time, and whether it was confirmed | `~/Library/Application Support/org.keyswitch.KeySwitch/history.json`. Plain JSON readable only by your user account. It is included in Time Machine backups. | **Off.** You must turn it on and confirm. Turning it off, or choosing *Delete all history*, deletes the file. Copies in existing backups remain. |
| Update state: time of the last check, your *Update Automatically* choice, and a downloaded update until it is installed | The preferences file above, and `~/Library/Caches/org.keyswitch.KeySwitch` | Always (when updates are on) |
| Usage statistics queue: daily counts and the random ID | `~/Library/Application Support/org.keyswitch.KeySwitch/telemetry.json`, readable only by your account | **Off.** Exists only while statistics are on. Deleted when you turn them off. |
| Diagnostics for the last 20 attempts | Memory only. Cleared when KeySwitch quits or when you choose *Clear*. | Always (in memory) |

History skips fields marked as secure and known password-manager apps. Apps don't always mark sensitive fields, so if you type sensitive text, keep history off.

## Diagnostics

The diagnostics report never contains your typed, selected or converted text, or clipboard content. It does contain:
- the bundle identifier of the app you were typing in (for example `com.google.Chrome`);
- times and timings;
- the type of text field;
- which replacement method was used;
- whether the text was Hebrew or Latin (not the text itself);
- numeric event traces.

The report leaves your Mac only if **you** copy it (*Settings → Advanced diagnostics → Copy Full Diagnostics Report*) and paste it somewhere, for example into a bug report.

## Permissions

KeySwitch asks for one permission: **Accessibility**. It has no entitlements, uses the hardened runtime, and is not sandboxed. The App Sandbox doesn't allow the Accessibility features KeySwitch needs. You can revoke the permission at any time in System Settings → Privacy & Security → Accessibility.

## Contact

Questions about privacy: open an issue in this repository. For anything sensitive, use the private reporting described in [SECURITY.md](SECURITY.md).
