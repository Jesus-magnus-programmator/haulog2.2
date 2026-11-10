HaulLog offline app - R&G Excavation  (version 39)
==================================================

This is the full HaulLog app as a web app that works with NO signal after the
first visit. PDF, Excel and ZIP exports are built in; nothing is downloaded
while you use it.

PUT IT ON GITHUB PAGES (one time, free)
---------------------------------------
1. Sign in at github.com. Click + (top right) > New repository.
   Name: haullog     Visibility: Public     then Create repository.
2. On the empty repository page click "uploading an existing file".
3. Unzip this zip. Open the folder and select EVERYTHING INSIDE it
   (index.html, manifest.webmanifest, sw.js, .nojekyll, README.txt and the
   icons folder) and drag it all onto the GitHub page.
   Important: index.html must be at the top level, not inside another folder.
   (If .nojekyll is hidden on your computer, skip it. The app still works.)
4. Click Commit changes.
5. Open the repository's Settings tab (not your account settings) > Pages.
   Under "Build and deployment" set Source = Deploy from a branch,
   Branch = main, Folder = / (root), then Save.
6. After 1-2 minutes the Pages screen shows your link:
   https://YOURNAME.github.io/haullog/

INSTALL ON EACH IPHONE
----------------------
1. Open the link in Safari while you have signal.
2. Share (square with up arrow) > Add to Home Screen > Add.
3. Open HaulLog from the new icon and let it finish loading.
4. Allow Location and Camera when asked.
5. Test: turn on Airplane Mode and open the icon. It should open normally.

ALREADY INSTALLED THE OLD VERSION?
----------------------------------
Upload these files to the same repository (Add file > Upload files; GitHub
replaces the old ones), wait about 10 minutes, then open the app twice with
signal. The first open downloads the update in the background and the second
open shows it. Your saved records are kept. If it still looks old, export
your days first, delete the icon, and add it to the Home Screen again.

ACCESS KEY (used unless Google sign-in is turned on, see below)
--------------------------------------------------------
The first time the app is opened on a phone it asks for the access key. Paste it once and
tap Unlock; the phone remembers it. It asks again only if the app is deleted and installed
again (or the phone's saved website data is cleared). The same key is needed to delete a Trip
Record (Documents > Trip Records > Delete). The key is NOT stored in this app, only one-way
fingerprints of it. Keep the key private.

GOOGLE SIGN-IN (REQUIRED IN THIS VERSION)
-----------------------------------------
Employees sign in with their Google account. Only the accounts listed in access.json can get in. The
file that came in this folder already lists:
      jesus.rea@rgexcavationut.com
      office@rgexcavationut.com
and says "login": "google", so the access key is no longer an alternative. The ONE thing still missing
is your Google "Client ID". Until you paste it in, the app shows "Google sign-in is not set up yet" and
nobody can use it.

If those two addresses are not Google accounts yet: a Google account can be created for any email
address (accounts.google.com/signup, choose "Use my existing email address"), or by your Google
Workspace admin if the company uses Workspace. Each person signs in with that account.

One-time setup (about 10 minutes, free):
 1. Go to console.cloud.google.com, sign in with the company Google account and create a project
    (name it HaulLog).
 2. APIs & Services > OAuth consent screen: choose Internal if rgexcavationut.com is a Google
    Workspace domain (Google then refuses everyone outside the company by itself), otherwise External.
    App name HaulLog, your email as support and developer contact, then Save. No scopes are needed.
    If you chose External you can leave it on Testing and add the two addresses under Test users;
    Google then refuses everyone else by itself too.
 3. APIs & Services > Credentials > Create credentials > OAuth client ID > Web application. Under
    "Authorized JavaScript origins" add  https://YOURNAME.github.io  (only that: no /haullog and no
    trailing slash; YOURNAME is your GitHub user name). Create it and copy the Client ID (it ends with
    .apps.googleusercontent.com).
 4. In GitHub open your haullog repository, click access.json, then the pencil (edit). Paste the Client
    ID between the quotes after "clientId": and click Commit changes. Each phone picks it up the next
    time the app is opened with a signal (allow up to about 10 minutes for GitHub to publish it).
Then open the app on a phone and tap "Sign in with Google".

What the settings mean (access.json):
 - allowedEmails: the exact Google addresses that may sign in (capital letters do not matter).
 - allowedDomains: for example "rgexcavationut.com" would let everyone at that company domain in.
   Left empty here, so ONLY the two addresses above can sign in.
 - adminEmails: always allowed, and the only accounts that can delete a Trip Record (they just
   confirm, no key). Left empty: every approved account can delete (with a confirmation).
 - keyFallback: false means there is no access key at all. If Google sign-in turns out not to work
   on a particular iPhone, you can set it to true to add a "Use the access key instead" button.
To add or remove someone: edit allowedEmails on GitHub and commit. The next time that phone opens the
app with a signal, a removed person is signed out. A phone that has not been online for more than 30
days has to connect before it can be used. Offline in between is fine. Sign out: Projects tab >
Signed in > Sign out.
When you update the app later, upload the new files but do NOT replace your access.json.
The first time this version opens on a phone it erases that phone's saved data once, so everyone
starts clean and has to sign in.
Be aware: this stops casual use and shows who signed in, but the app runs on each phone and the
files are public on GitHub, so it cannot stop someone technical who copies the app. Trip data is only
stored on each phone, so there is nothing shared to steal. Erase all app data still uses the admin key.

WHAT'S NEW IN VERSION 39
------------------------
Timesheet
- New layout in the style of a DOT driver time record: logo and centered title, a compact info grid
  (driver, date, sheet no., truck, project, client, odometer start → end, loader, all loading and
  unloading locations, work overview), then the driver log.
- Driver log: No. · Load Time (Start loading) · Route (loading → unloading) · Material · Delay code.
  The first row is the travel to the jobsite. When loads repeat the same route, an arrow line marks
  them "same as above".
- More than 25 loads: page 1 fills with loads and the log continues on the next pages. Totals,
  comments, certification and signature always come after the last load.
- Totals: Travel time + Working hours − Downtime = TOTAL TRUCK HOURS, plus Total loads. Note: if
  applicable under the agreement, travel time is adjusted on the invoice.
- Comments / Pauses are never cut off; long comments continue on the next page.
- Tap the Timesheet chip on the Today screen to open the timesheet full screen (PDF, zoom, share).

Trip
- New step "Start loading". Loads count once delivered.
- More menu (with icons): Undo last event (reason required, saved to Excel), Early signature
  (client approves hours before the last load; the driver picks an estimated clock-out time; only one
  more load can be recorded; the real clock-out time and GPS are added to the comments), Clock out
  (the client signs the driver out now, available at any step, reason required), Cancel whole trip.
- "Hauling now" card shows the material and route of the load on the truck.
- Comments, client name and odometer on the sign-off card are saved as you type.

Photos
- Pre-trip and post-trip need at least 4 truck photos, taken with the in-app camera (several in a
  row, then Done). Truck and defect photos get the date, time and GPS printed on them.
- Fuel tab: take one or more receipt photos per fill-up. Fuel is no longer entered in the post-trip.
- Every photo's time and GPS is listed in the Excel "Photos" sheet.

Map
- Trip events panel has Events and Map tabs. The map has a timelapse slider and play button.

Look
- Refreshed design: softer cards, rounded controls, line icons for the camera buttons.

WHAT'S NEW IN VERSION 38
------------------------
- Load steps: Arrive at loading site > Loading began > Depart with load > Arrived at unloading site >
  Load delivered (or Final load delivered). A load only counts as hauled once it is delivered.
- Load details (material, loading and unloading location, delay) can be changed until the load is
  delivered: tap the Load details chip while the load is on its way. Ticket photos can also be added
  or removed until delivery. The ticket camera now opens the front (selfie) camera.
- Downtime reasons are now only: Accident, Mechanical / equipment, Other.
- Timesheet: TRAVEL TIME + WORKING HOURS - DOWNTIME = TOTAL TRUCK HOURS, with a note that downtime
  is not counted towards total truck hours. The sign-off text ends at "ready to be billed and paid."
- Tap any document preview (timesheet, inspection reports, fitness checklist) to open it full screen.
  Pinch, double-tap, or use the + and - buttons to zoom. PDF and Share buttons are at the top.
- Location every 2 minutes plus a map in the Trip events panel (see LOCATION AND TRIP MAP).
- Keep screen on (see KEEP SCREEN ON).
- The Today card no longer shows the project/vehicle/odometer line, the "Last event" time or the
  hours driven line. The Events chip was removed (swipe right or tap the left edge tab instead).

LOCATION AND TRIP MAP
---------------------
Turn Location on in the Projects tab. While a trip is open, the phone saves your position every
2 minutes and also each time you tap an event (arrive, loading began, depart, arrived at unloading,
delivered, downtime and so on). The Trip events panel (swipe right) shows a map at the top: the blue
line is your route, the dots are the events (orange = loading site, blue = unloading site, green =
delivered, red = downtime, grey = yard). Tap a dot for its name and time, or tap "Show on map" under
an event. "Hide map" gives the list more room.
The map pictures come from OpenStreetMap and need signal. Without signal the route and dots are still
drawn on a plain background, and nothing is lost. Positions appear in the Excel export (Events sheet
and a new "Route (every 2 min)" sheet), never on the timesheet or other PDFs.
Important: an iPhone only lets a web app use location while the app is open on the screen. If the
app is closed or the phone is locked, no positions are saved for that time. Keep the screen on (below).

KEEP SCREEN ON
--------------
On by default (Projects tab > Keep screen on). While HaulLog is open on the screen, the phone does
not go to sleep. Keep the phone on a charger in the truck. If the card says the phone can't keep the
screen on, update iOS; older versions do not allow it for Home Screen apps.

LOAD TIME ON THE TIMESHEET
--------------------------
The Load Time column of the timesheet shows the time Start loading was tapped for each load.

IMPORT TRIP RECORDS FROM A ZIP
------------------------------
Documents tab > Import Trip Records > Choose ZIP file(s). Pick Trip Record ZIPs made with Export (ZIP)
(several at once, or one ZIP that holds several). Every ZIP exported from this version on contains
HaulLog-data.json, which is what lets the full record come back: events, downtime, signatures,
inspection reports, ticket photos, fuel and the fitness checklist days. ZIPs made by older versions
have no data file and cannot be restored. Records already in the app are skipped, and a record that
was still in progress when exported is skipped.

LOAD TICKET PHOTOS
------------------
At the loading site, before Depart with load, the Today screen has a Load ticket card.
Tap Take ticket photo (rear camera) as many times as needed. The photos stay with that
load and show in the events list. They are added to the timesheet PDF as extra pages
(2 tickets per page, as many pages as needed) and are also in Export (ZIP) as a Tickets
folder of the original photos. They are stored on the phone and removed when the Trip
Record is deleted.

ERASE ALL APP DATA
------------------
Documents > Erase all app data. It needs the ADMIN key (different from the driver's access
key). It deletes EVERYTHING on that phone: Trip Records, ticket photos, fitness checklists,
projects, vehicles, trailers, clients, locations and settings, and it removes permission to
use HaulLog, so the app asks for the access key again. It cannot be undone. Export anything
you need first. The admin key is NOT stored in this app, only a one-way hash.

TRIP EVENTS PANEL
-----------------
The events of the current trip are no longer shown on the Today screen. While a trip is in progress,
swipe right anywhere on the Today, Projects or Documents screens, or tap the bright tab on the left
edge, to open the Trip events panel. It shows the trip map (see LOCATION AND TRIP MAP) and lists every
event, newest first, with its time, the minutes since the previous event, material, loading and
unloading locations, delay notes and ticket photos, and any downtimes (in time order with the
events), plus loads hauled, events so far, the latest event and the next step. Back (or a swipe
left on the panel's top bar) closes it. It is not available when no trip is in progress. Swipes
that start on a signature pad, a typing box, or the very edge of the screen are ignored.
(The in-app map and the Navigate button were removed.)

PROJECTS
--------
Each project has ONE client, a main Loading location and a main Unloading location, and optional
lists of "More loading locations" and "More unloading locations". When a project is selected at
the start of the day the loading and unloading locations are already filled in with the project's
main ones (change them if needed); the client is shown and cannot be changed there. In Load
details during a trip only the project's own locations are offered. The "+ New" buttons add a
location to the selected project. Add and edit all of this in the Projects tab: use the pen icon on
a project to edit it. Past Trip Records keep the project details they were made with.
(When an earlier version is updated, extra clients are dropped and the old shared location lists
are moved into the projects once.)

CLOCK IN
--------
Every day starts with Clock in. Until the driver taps Clock in, the Today screen shows only the
Clock in card (no Start workday section). After clocking in, the Start workday section appears;
fill it in and tap Begin today's record. The clock-in time is kept with the day and the hours count
from it. "Undo clock-in" cancels it (Start workday disappears again). A clock-in left over from an
earlier day is discarded.

INSPECTIONS (PRE-TRIP AND POST-TRIP)
------------------------------------
The Address on pre-trip and post-trip reports is filled in as plain text with 2584 W 3100 N, Farr
West, UT 84404 (it can still be edited).
A pre-trip report can always be signed, even with a defect (the defect must be described in
Remarks). The mechanic's signature is optional and never needed to sign. If a defect is not cleared
(not marked Corrected or Not required, and not repaired by a mechanic with the mechanic's
signature), the trip cannot be started: the app says "Do not start the trip yet", gives buttons to
save/share the pre-trip report PDF to send to the office, and keeps Depart yard locked. Three
options are offered:
 - "Defect cleared: do another pre-trip": after the defect on the power unit and/or trailer has
   been repaired, confirm it (the question names the unit that had the defect) and a new pre-trip
   report is started for the SAME truck and trailer. The failed report stays in the record.
 - "Change power unit or trailer": choose another truck and/or trailer; a new pre-trip report for
   the new unit must be signed before Depart yard unlocks.
 - "Cancel this trip and clock out": asks for the reason; the trip is cancelled and the hours count
   until then.
The failed and earlier pre-trip reports stay in the record and in the Export ZIP, and the Trip
events panel lists each unit change / cleared defect. Another pre-trip can only be done before the
truck leaves the yard. In the post-trip report each
defect must still be marked (reported for repair or not required); there is no mechanic signature
there.

BOTTOM BAR, FUEL AND HOURS
--------------------------
The bottom bar has five icons: truck = Today, folder = Projects, page = Documents, fuel pump = Fuel,
clock = Hours worked.
Fuel records only two things: the gallons put in the vehicle and the price per gallon. Both are
required. Fuel can be entered once a trip for that day has started (a cancelled trip cannot get
fuel):
 - in the post-trip report there is an optional "Fuel added" section (gallons and price per gallon).
   If gallons are entered, the price per gallon must be entered before the report can be signed
   (or clear the gallons); or
 - on the Fuel tab choose the trip (today's trip is listed as soon as it has started, marked "in
   progress"), enter the gallons and the price per gallon and save.
Each entry on the Fuel tab shows the date, project, vehicle, gallons, price per gallon, total cost,
and next to the gallons: miles per gallon (trip miles from the odometers / gallons), fuel used per
billable hour (gal/hr) and fuel cost per billable hour ($/hr). A dash means it cannot be worked out
(no odometer miles, no billable hours, or no price). There are no fuel statistics, graphs or
summaries. "Fuel log (Excel)" exports the entries including those three figures; the per-day Excel
has a Fuel sheet and "Fuel added (gal)" / "Fuel price per gallon" columns on Days. Deleting a Trip
Record also deletes its fuel entry.
Hours driven (clock icon): each day counts from clock-in (or the start of the pre-trip if you did
not clock in first) to clock-out, including the pre-trip, post-trip, waiting and downtime. Weeks
start on Monday and pay is every two weeks (a pay period is two weeks in a row, starting Monday
Sep 28, 2026 and every 14 days from then: Oct 12, Oct 26, ...). Choose a week in the Week drop-down
to see its days and its total; the Pay period card shows the two weeks of the period that contains
that week and their total. Two trips on the same date are added together. A cancelled trip counts
until it was cancelled, a trip ended early counts until it ended, and a trip still going shows "in
progress" with the hours so far.
Driver driven time is not shown in the load records (Trip Records and Excel); those keep only the
trucking hours charged to the client.

CLIENT APPROVAL OF THE HOURS
----------------------------
When the client signs off the hours at the final delivery, the signed timesheet opens straight away,
the same way a pre-trip or post-trip report opens after it is signed: heading "Signed timesheet",
who approved it and when, the PDF / Share buttons and the document preview. Tap Back to return to
the Today screen for the next step (Return to yard).

ODOMETER READINGS
-----------------
Required: the reading when the pre-trip starts, and the reading at client sign-off.
Optional: the reading after the post-trip (shown when you clock out). Leave it empty to skip.
If you do type one it must still be a number, and a reading lower than the earlier ones asks you
to confirm. Without it, miles in the Fuel statistics come from the sign-off reading.

GOOD TO KNOW
------------
- Always open the app from the Home Screen icon (the Safari tab keeps separate
  records). Deleting the icon deletes that phone's records, so export first.
- Records live on each phone only. Use "Export day" (ZIP) to send a day to the
  office; offline, it sends once the phone has a connection.
- GPS coordinates are saved every 2 minutes and with each action. They appear on the trip map and in
  the Excel file, never on the timesheet.
- To update later: upload the new files, then change VERSION in sw.js
  (for example "haullog-v39") so phones replace their saved copy.
