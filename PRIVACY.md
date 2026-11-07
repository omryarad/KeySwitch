# Privacy

**Short version:** KeySwitch works entirely on your Mac. Your text never leaves it. Its network requests are a daily check for updates on GitHub (you can turn it off) and **usage statistics**: counts and a random installation ID, never text. Statistics are on by default after a short notice (in the EU, EEA, UK and Switzerland they are asked for first), and you can turn them off at any time without losing any feature. Conversion history is off unless you turn it on.

This statement describes KeySwitch from version 0.2.1 (build 21, the first version with usage statistics).  Build 18 has the update check only; build 17 and earlier have no network code at all. It was written from a review of the app's source code, not as a marketing summary. If a future version changes any of this, this page will change with it.

The sections below describe **KeySwitch for Mac**. **KeySwitch for Windows** works differently (for one, it sends no usage statistics): see [KeySwitch for Windows](#keyswitch-for-windows).

## What KeySwitch accesses, and when

| What | When | Why |
|---|---|---|
| The selected text and the field's text in the active app (Accessibility) | Only after you press the KeySwitch shortcut | To read what you selected, convert it, and check afterwards that the replacement really happened. The text is held in memory only for that operation. |
| Keyboard events (Copy / Paste) sent to the active app | Only during a conversion, in apps that need it (mostly browsers) | Some apps only accept a replacement through their own Copy and Paste. |
| Your clipboard | Only during such a Copy/Paste conversion | KeySwitch saves your current clipboard in memory, uses the clipboard for about a second, then puts your content back. It only restores it if nothing else has changed the clipboard in the meantime. |

KeySwitch does **not**:
- access the network for anything except the update check and, while they are on, the usage statistics described below;
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

## Usage statistics

From version 0.2.1, KeySwitch sends usage statistics to show whether conversion works, where it fails and how to improve it. They are not used to track you or build a profile.

- **On by default, and you can turn them off at any time** in *Settings → Privacy → Share usage statistics*. KeySwitch works exactly the same with them off.
- **Shown before anything is sent.** At first launch, and on the first launch after updating from Beta 2.0, a short notice explains this. Nothing is collected before it is answered.
- **Asked first in Europe.** On Macs whose region (System Settings → General → Language & Region) is set to a country in the EU, the EEA, the UK or Switzerland, the notice asks first (*Allow* or *Not Now*), and statistics stay off unless you allow them. The region setting is used, not your location.
- *Settings → Privacy → What Is Sent…* shows the exact data waiting to be sent.

| What | Details |
|---|---|
| What is sent | Daily counts of shortcut presses and of conversions that succeeded, were not confirmed, or failed. The failure reason, from a fixed list (for example "no selection", "the app did not accept the replacement"). The conversion direction (Hebrew→English or English→Hebrew). The replacement method. The duration in coarse buckets (for example 100–250 ms). The **kind** of app (browser, messaging, AI app, code editor, Apple app, other). The KeySwitch version and build, the macOS version (for example 15.1), the update channel, and the local date. |
| Identifier | A random installation ID, created when statistics start, used only to count active installations and retention. It is persistent, so the data is **pseudonymous, not anonymous**. It is not derived from your Mac, your account or anything else, and is not linked to your name. On the server it is stored only as a keyed hash. |
| What is never sent | The text you select, convert or type. Clipboard content. Passwords (password fields are refused before anything is read). App names or bundle identifiers. Window titles, document names, document content or URLs. Your name, user name, computer name, email, hardware identifiers, language or time zone. |
| When | At most once an hour, in the background. Sending never delays or affects a conversion. If you are offline, up to 35 days are kept on your Mac (`~/Library/Application Support/org.keyswitch.KeySwitch/telemetry.json`, readable only by your account) and sent later. Older days are dropped. |
| Where | A server run by KeySwitch's developer on Cloudflare Workers (a hosting provider), over HTTPS. The database is in Cloudflare's European region. Cloudflare processes your IP address to deliver the request. KeySwitch's server does not store IP addresses and keeps no request logs. Cloudflare's own privacy policy covers its processing. |
| Retention | Statistics are deleted after 400 days. |
| Turning them off | *Settings → Privacy → Share usage statistics*. Sending stops at once, the ID and the queued data on your Mac are deleted, and the server is asked to delete everything stored for that ID. If your Mac is offline at that moment, KeySwitch repeats the request the next time it starts, until the server confirms it. No new ID is created while statistics are off. Turning them on again creates a new, unrelated ID. |
| Who sees it | Only the developer, through a private dashboard behind sign-in. Statistics are not sold or shared. Aggregated totals (for example "N active installations") may be published. |

### Who is responsible, and your rights

KeySwitch's developer decides what is collected and why, and is responsible for it. Under Israel's Protection of Privacy Law you may ask to see the information held about your installation and to have it corrected or deleted. Because the server knows only a hashed random ID, include the ID shown in *Settings → Privacy → What Is Sent…* in your request. Turning statistics off deletes the data without any request. Requests and questions: **omry@taskirim.com**. You will get an answer within 30 days.

## Data stored on your Mac

| Data | Where | Default |
|---|---|---|
| Settings: language, shortcut, options, whether the guide was completed | `~/Library/Preferences/org.keyswitch.KeySwitch.plist` | Always |
| **Conversion history**: original and converted text, time, and whether it was confirmed | `~/Library/Application Support/org.keyswitch.KeySwitch/history.json`. Plain JSON readable only by your user account. It is included in Time Machine backups. | **Off.** You must turn it on and confirm. Turning it off, or choosing *Delete all history*, deletes the file. Copies in existing backups remain. |
| Update state: time of the last check, your *Update Automatically* choice, and a downloaded update until it is installed | The preferences file above, and `~/Library/Caches/org.keyswitch.KeySwitch` | Always (when updates are on) |
| Usage statistics queue: daily counts and the random ID | `~/Library/Application Support/org.keyswitch.KeySwitch/telemetry.json`, readable only by your account | Exists only while statistics are on. Deleted when you turn them off. |
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

## KeySwitch for Windows

This describes KeySwitch for Windows from version 0.1.0-beta.1, also written from a review of its source code.

| | |
|---|---|
| Usage statistics | **None.** The Windows version has no statistics code and no installation ID. |
| Network | Only when you choose *Check for Updates*: one request to GitHub's public API for the list of KeySwitch releases. GitHub receives your IP address, as with any visit to GitHub ([GitHub's privacy statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement)). Nothing about you or your text is sent. Links in the app (help, privacy policy) open in your browser. |
| What it reads, and when | Only when you press the shortcut: the text selected in the active window, through Windows UI Automation (the accessibility interface) or, where an app doesn't offer it, that app's own Copy. Password fields, terminal windows and apps running as administrator are skipped. |
| Clipboard | To paste the converted text, KeySwitch puts it on the clipboard for a moment, marked so that Windows clipboard history and cloud clipboard skip it. Shortly after the paste (usually within a second, at most about 3 seconds) it puts back everything you had, unless you copied something new in the meantime. If your clipboard holds content a password manager marked as private, KeySwitch doesn't touch it and doesn't convert. If KeySwitch is closed in that moment, your previous clipboard may not come back. |
| Stored on your PC | `%APPDATA%\KeySwitch\settings.json` (language, shortcut, options). If you turn on conversion history (off by default): `%APPDATA%\KeySwitch\history.bin`, encrypted with Windows DPAPI for your Windows user only. Turning history off deletes it. |
| Diagnostics | The last 50 attempts, in memory only (outcome, method, the app's process name such as `chrome`, timings; never text). It leaves your PC only if you copy the report and paste it somewhere. |
| Permissions | None to grant. KeySwitch runs as your user and never asks for administrator rights. "Start when I sign in" adds one value under `HKEY_CURRENT_USER\…\Run`. |
| Uninstalling | Removes the app, the sign-in entry, the settings and the history. |

## Contact

Privacy questions and requests (access, correction, deletion): **omry@taskirim.com**. Security vulnerabilities: the private reporting described in [SECURITY.md](SECURITY.md).
