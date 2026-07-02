# Workforce — Attendance, Occurrence & Make-Up Tracker

One single, self-contained `index.html`. No build, no install, no server. Runs on Windows, macOS, iOS, Android, and every major browser (Edge, Chrome, Safari, Firefox).

## Quick start

Open `index.html` in any browser. It loads with sample data so you can explore immediately.

## Deploy free with GitHub Pages

1. Create a repo on GitHub (e.g. `workforce`) and push this folder.
2. Repo → **Settings → Pages** → Source: *Deploy from a branch* → Branch: `main`, folder `/ (root)` → Save.
3. Your team opens `https://<your-username>.github.io/workforce/` on any device.

```bash
git remote add origin https://github.com/<your-username>/workforce.git
git push -u origin main
```

## Connect your Microsoft Forms data (automated)

The app pulls straight from the Excel workbook that Microsoft Forms writes to:

1. In OneDrive/SharePoint, open the Forms results workbook → **Share** → *Anyone with the link can view* → copy link.
2. In the app: **Settings → Live data link** → paste → **Save & sync now**.
3. Leave **Auto-sync on load** checked — every time anyone opens the app, it pulls the latest data.

If your tenant blocks anonymous links, use **Settings → File import** to drop in the `.xlsx` export instead.

## Data format

Column names are matched flexibly ("Emp ID", "Attendance Type", "Comments" all work). See `workforce-template.xlsx` for a ready-made starting point.

**Employees sheet** (sheet name containing "Employees"/"Roster"): Employee ID, Name, Department, Team, Title, Supervisor, Manager, Senior Manager, Location, Status.

**Attendance sheet** (any other sheet, including raw Forms exports): Date, Employee ID (or Name), Type, Hours, Notes. Recognized types with common synonyms: Present, Absent (no call no show, call out), Tardy (late), Short Shift (left early), FMLA, LOA (leave of absence), PTO Approved (vacation), PTO Unapproved, Make-Up.

## What it tracks

Attendance rate, perfect attendance, absences, tardies, short shifts, FMLA, LOA, approved and unapproved PTO, occurrences, and make-up time — filterable by day/week/month/quarter/annual/adjusted period and by department, team, title, supervisor, manager, and senior manager.

**Corrective ladder** (rolling 90 days): 3 occurrences → Verbal, 4 → Written, 5 → Final, 6 → Termination Eligible.

**Make-up time / OSS.** An OSS (Out / Short-Shift) is a mulligan: instead of taking an occurrence or losing pay, an agent agrees to make up the missed time. Each agent gets up to 3 OSS per rolling 12 months. Flow: *Pending → Approved → Completed* (linked occurrence is waived) or *Missed* (occurrence stands). Admins create and manage agreements on the Make-Up Time tab or from an employee's profile.

## Admin mode

Click **Admin** and enter the PIN (default `2468` — change it in Settings). Admins can add/edit/delete records (including from the calendar), and create/approve/complete make-up agreements. Everyone else gets a read-only view.

Note: the PIN is a convenience gate for a static page, not real security. Anyone with the underlying Excel link can see the data — share accordingly.

## Where edits live

Imported data is refreshed from your Excel link on every sync; records added in-app are kept separately and survive re-syncs. Everything is stored in the browser (localStorage) per device. Use **Settings → Download backup** to move data between devices or keep an offline copy.
