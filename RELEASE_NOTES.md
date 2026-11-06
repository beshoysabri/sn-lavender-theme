fix: accessory tint 1 follows the accent; install from the desktop app

v2.5.0 left accessory tint 1 at the native #086dd6, treating it as a
categorical icon colour. In the running app it is the most visible colour
after the accent: Standard Notes tints the Super, plain-text and rich-text
note icons with it, and pairs it with info-faded fills in the note's
editing-status pill — the app is built on tint 1 matching the default blue
accent. Dark Blue gets that match for free. Lavender now sets tint 1 to
#a79ef4, so no blue is left over; the other five tints stay native.

Docs: Install Custom Plugin lives under Preferences → Plugins in current
Standard Notes (v3.203.0), not General → Advanced Settings. The README and
landing page now say so, and say to install from the desktop app: the web
app's CSP only allows plugin links from Standard Notes' own servers and
raw.githubusercontent.com, and the latter is refused anyway because the
request is credentialed and GitHub answers Access-Control-Allow-Origin: *.
That holds for every self-hosted theme, Dark Blue included. Installed themes
sync, and the web app loads the stylesheet and fonts from Pages without
complaint once installed — verified against app.standardnotes.com.

deploy.sh: strips the \r that native Windows curl leaves on its write-out,
which made a healthy deploy report broken font assets on Windows.

CI: colour digest re-baselined for tint 1 — still 90 declarations.

Released as 2.5.1.
