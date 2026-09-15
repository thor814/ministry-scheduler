MINISTRY SCHEDULER — INSTALLABLE, SYNCED APP
=============================================

This folder is a complete, ready-to-host app:
  index.html
  manifest.json
  sw.js
  icons/icon-192.png
  icons/icon-512.png
  README.txt (this file)

It syncs live across everyone who uses it, using a free Firebase
database. There are three one-time steps: create the database,
put the app online, then install it.


STEP 1 — Create a free Firebase database (~5 minutes)

  1. Go to https://console.firebase.google.com and sign in with
     any Google account.
  2. Click "Add project", give it a name (e.g. "ministry-scheduler"),
     and finish the wizard (you can turn off Google Analytics —
     not needed).
  3. In the left sidebar, click "Build" > "Realtime Database".
  4. Click "Create Database". Choose any location. When asked
     about security rules, choose "Start in test mode" for now.
  5. Once created, click the "Rules" tab and replace the contents
     with:

       {
         "rules": {
           "ministry-scheduler-state": {
             ".read": true,
             ".write": true
           }
         }
       }

     Click "Publish". (This means anyone with your app's link can
     read and write the schedule — there's no login system. That's
     fine for a small team using a private link, but don't post the
     link publicly. Let me know if you'd like a login step added.)

  6. In the left sidebar, click the gear icon > "Project settings".
  7. Scroll to "Your apps", click the "</>" (web) icon to register
     a new web app. Give it any nickname and click "Register app".
  8. Firebase will show you a firebaseConfig object with values
     like apiKey, authDomain, databaseURL, etc. Copy the whole thing.


STEP 2 — Paste your config into the app

  1. Open index.html in any text editor (Notepad, TextEdit, VS Code).
  2. Find this block near the top of the script (search for
     "PASTE_YOUR"):

       const firebaseConfig = {
         apiKey: "PASTE_YOUR_API_KEY",
         ...
       };

  3. Replace it with the config object Firebase gave you in Step 1.
  4. Save the file.


STEP 3 — Put it online (pick ONE option)

Option A: GitHub Pages (free forever)
  1. Create a free account at github.com if you don't have one.
  2. Create a new repository (e.g. "ministry-scheduler").
  3. Upload all the files in this folder (including the icons
     folder) using "Add file" > "Upload files".
  4. Go to the repo's Settings > Pages.
  5. Under "Source", choose the main branch and save.
  6. You'll get a URL like:
     https://yourusername.github.io/ministry-scheduler/

Option B: Netlify Drop (fastest, no coding)
  1. Go to app.netlify.com/drop
  2. Sign up for a free account if prompted.
  3. Drag this whole folder onto the page.
  4. Netlify gives you a live URL right away.


STEP 4 — Install it

On a phone (iPhone/Android):
  1. Open your URL in Safari (iPhone) or Chrome (Android).
  2. Tap Share (iPhone) or the menu (⋮) (Android).
  3. Tap "Add to Home Screen".

On a computer (Chrome, Edge):
  1. Open your URL.
  2. Click the install icon in the address bar, or use the browser
     menu > "Install Ministry Scheduler".

Share the same URL with every lead/admin — everyone who opens it
(installed or not) sees and edits the same live schedule.


TROUBLESHOOTING
- If you see "One setup step left" when you open the app, the
  firebaseConfig block still has placeholder text in it — go back
  to Step 2.
- If changes don't appear on another device, check the Rules tab
  in Firebase matches Step 1.5 exactly, and that both devices are
  using the exact same hosted URL.
