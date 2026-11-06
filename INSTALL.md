# Installing KeySwitch

## Install

1. Download **[KeySwitch-0.2.1.dmg](https://github.com/omryarad/KeySwitch/releases/download/v0.2.1-beta/KeySwitch-0.2.1.dmg)** (KeySwitch Beta 2.1), or the DMG of any newer version from [Releases](../../releases). You don't need the `.zip` file: it's used by automatic updates.
   Optionally, check its checksum against `SHA256SUMS.txt` in the same release:
   ```bash
   shasum -a 256 ~/Downloads/KeySwitch-*.dmg
   ```
2. Open the DMG. A window shows **KeySwitch** and an **Applications** folder.
3. Drag **KeySwitch** onto **Applications**.
4. Eject the DMG, then open **KeySwitch** from your Applications folder.
   macOS may ask you to confirm opening an app downloaded from the internet. KeySwitch is signed with a Developer ID and notarized by Apple.
5. The welcome guide opens. It will:
   - explain what KeySwitch does;
   - help you allow **Accessibility** access. You'll see one macOS dialog: choose **Open System Settings**, turn on **KeySwitch**, and come back. The guide notices the change by itself;
   - show your shortcut (**⇧⌘J** by default) and let you change it;
   - give you a practice field to try a conversion.

KeySwitch then lives in the menu bar (the ⇄ icon: two opposing arrows). There is no Dock icon. To open Settings, click the menu bar icon.

## Start at login (optional)

Menu bar icon → **Launch at login**, or the same switch in Settings. This is off by default.

## Update

From KeySwitch Beta 2.0 on, updates are automatic: KeySwitch checks GitHub once a day, downloads a new version in the background and installs it when you quit KeySwitch. You can also choose **Check for Updates…** in the menu bar menu, or turn off **Update Automatically** there. Your shortcut, settings, history and Accessibility permission are kept.

Coming from an older version without automatic updates? Download the new DMG once and drag KeySwitch onto Applications, choosing **Replace**.

If KeySwitch stops converting text after a manual update from 0.1.x, macOS may need you to re-approve it. Open System Settings → Privacy & Security → Accessibility, remove **KeySwitch** with **−**, then open KeySwitch again and follow the guide.

## Uninstall

1. Menu bar icon → **Quit KeySwitch**.
2. Drag **KeySwitch** from Applications to the Trash.
3. Optionally remove its data. To delete your usage statistics on the server too, first turn off *Settings → Privacy → Share usage statistics*.
   ```bash
   rm -rf ~/Library/Application\ Support/org.keyswitch.KeySwitch
   defaults delete org.keyswitch.KeySwitch
   ```
4. Optionally remove it from System Settings → Privacy & Security → Accessibility.

## Troubleshooting

| Problem | What to do |
|---|---|
| Nothing happens when I press the shortcut | Check the menu bar icon's status line. If it says permission is missing, open the welcome guide from Settings. |
| "This shortcut is in use" | Choose another shortcut in Settings. Some shortcuts are reserved by macOS or by other apps. |
| A web page field in Chrome didn't change | This is a known beta limitation in some web page fields, such as the Google and YouTube search boxes (see the README). Chrome's address bar works. Try again, or turn on Settings → Advanced diagnostics → *Always replace by pasting*. Please [report it](../../issues/new?template=bug_report.yml). |
| Password fields | KeySwitch never works in password fields. This is intentional. |

---

<div dir="rtl" lang="he">

## עברית

### התקנה
1. מורידים את **[KeySwitch-0.2.1.dmg](https://github.com/omryarad/KeySwitch/releases/download/v0.2.1-beta/KeySwitch-0.2.1.dmg)** (KeySwitch Beta 2.1), או את ה־DMG של גרסה חדשה יותר מ־[Releases](../../releases). אין צורך בקובץ ה־`.zip`: הוא משמש את העדכונים האוטומטיים.
2. פותחים את ה־DMG: מופיע חלון עם **KeySwitch** ותיקיית **Applications**.
3. גוררים את **KeySwitch** אל **Applications**.
4. מוציאים את ה־DMG ופותחים את **KeySwitch** מתיקיית היישומים. ייתכן ש־macOS יבקש אישור לפתיחת אפליקציה שהורדה מהאינטרנט. KeySwitch חתומה ב־Developer ID ועברה נוטריזציה של Apple.
5. מדריך הפתיחה נפתח:
   - בשלב ההרשאה יופיע חלון אחד של macOS. בוחרים בו **פתיחת הגדרות המערכת**, מפעילים את **KeySwitch** וחוזרים. המדריך יזהה את השינוי לבד;
   - הקיצור כברירת מחדל הוא <bdi>⇧⌘J</bdi>, ואפשר להחליף אותו;
   - יש שדה תרגול לניסיון המרה.

אחרי ההתקנה KeySwitch נמצאת בשורת התפריטים (סמל ⇄ של שני חצים מנוגדים), בלי סמל ב־Dock.

### עדכון
מ־KeySwitch Beta 2.0 העדכונים אוטומטיים: פעם ביום KeySwitch בודקת ב־GitHub, מורידה גרסה חדשה ברקע ומתקינה אותה כשיוצאים מהאפליקציה. אפשר גם לבחור **בדיקת עדכונים…** בתפריט, או לכבות שם את **עדכון אוטומטי**. הקיצור, ההגדרות, ההיסטוריה והרשאת הנגישות נשמרים.

מגיעים מגרסה ישנה בלי עדכון אוטומטי? מורידים פעם אחת את ה־DMG החדש, גוררים אל Applications ובוחרים **החלפה**. אם אחרי שדרוג ידני מ־0.1.x ההמרה הפסיקה לעבוד: בהגדרות המערכת ← פרטיות ואבטחה ← נגישות, מסירים את KeySwitch עם **−**, פותחים אותה שוב ועוברים על המדריך.

### הסרה
יוצאים מ־KeySwitch (סמל שורת התפריטים ← יציאה), גוררים את האפליקציה לפח, ואם רוצים מוחקים גם את הנתונים בעזרת שתי הפקודות שבחלק האנגלי למעלה. כדי למחוק גם את סטטיסטיקות השימוש מהשרת, כבו קודם את הגדרות ← פרטיות ← שיתוף סטטיסטיקות שימוש.

</div>
