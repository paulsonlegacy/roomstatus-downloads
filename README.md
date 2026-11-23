# MyRoomStatus — Offline Setup Guide

This guide walks you through setting up MyRoomStatus to run on your hotel PC,
without needing an internet connection to do your daily work.

---

## What is Offline Mode?

Offline mode lets your hotel run MyRoomStatus entirely on your own Windows PC.
You can take bookings, manage check-ins, run POS, and handle daily operations
even when there is no internet. When internet is available, you sync your data
to the cloud with one click.

---

## Before You Start

Make sure you have:

- Your **hotel code** (e.g. `RS-ABCD1234`) — found on your cloud dashboard
- Your **admin email and password** for MyRoomStatus
- An active MyRoomStatus **subscription**
- The **MyRoomStatus offline installer** (`RoomStatus.exe`) — provided by your account manager

---

## Step 1 — Switch Your Hotel to Offline Mode

Do this from the **cloud version** of MyRoomStatus (the one you normally open in your browser).

1. Log in to MyRoomStatus on the cloud as usual.
2. Go to **Settings → Operation Settings**.
3. Change the operation mode to **Offline**.
4. Save the change.
5. **Log out** of the cloud.

> This tells the cloud to stop accepting new bookings and operations from the
> browser. From now on, all daily operations happen on your PC.

---

## Step 2 — Verify the Download (Optional but Recommended)

Before installing, you can confirm the file has not been corrupted or tampered with
by checking its SHA256 checksum against `SHA256SUMS.txt` (provided alongside the installer).

**Ubuntu or Mac:**
```
sha256sum -c SHA256SUMS.txt
```

**Windows PowerShell:**
```
Get-FileHash RoomStatusOffline.zip -Algorithm SHA256
```
Compare the output hash to the value in `SHA256SUMS.txt`. They must match exactly.

---

## Step 3 — Install the Offline App on Your Windows PC

1. Locate the `RoomStatus.exe` file on your USB drive or in your downloads folder.
2. **Double-click** `RoomStatus.exe` to open it.
3. Windows may show a security warning — click **Run anyway** (or **More info → Run anyway**).
4. The app will open in your default web browser automatically.

> There is nothing else to install. No internet is needed after this point.

---

## Step 4 — First-Time Setup (One-Time Only)

The first time the app opens, you will see a **setup screen** asking for your hotel details.

1. Enter your **Hotel Code** (e.g. `RS-ABCD1234`).
2. Enter your **Admin Email** and **Password**.
3. Enter the **Cloud URL**: `https://api.myroomstatus.com`
4. Click **Set Up**.

The app will connect to the cloud, download all your hotel data (rooms, staff, settings),
and save everything to your PC. This requires internet **once** and takes about a minute.

> Once setup is complete, the setup screen disappears and the **login screen** appears.
> You will never see the setup screen again on this PC.

---

## Step 5 — Log In and Start Working

1. Log in with your email and password.
2. You are now inside MyRoomStatus running on your PC.
3. Use it exactly as you would the cloud version — bookings, check-ins, POS, reports, everything works.

> Internet is not required for day-to-day operations.

---

## Step 6 — Sync Your Data to the Cloud

After working offline, your data exists on your PC but not yet on the cloud.
Syncing sends your latest records up to the cloud so they are backed up and visible
from anywhere.

1. Look for the **sync icon** in the top navigation bar of the app.
   It shows a small number badge if there is data waiting to be synced.
2. Make sure your PC has internet.
3. Click the **Sync to Cloud** button.
4. Wait a few seconds. A message will confirm: **"Sync completed!"**

> You can sync as often as you like — daily is recommended.
> If sync fails, check your internet connection and try again.

---

## Everyday Use — Summary

| Task | Where |
|------|-------|
| Open the app | Double-click `RoomStatus.exe` |
| Log in | Enter your email and password |
| Take bookings, check-ins, POS | Works normally, no internet needed |
| Sync data to cloud | Click the sync icon in the top bar |

---

## Running on Multiple PCs

If you have more than one PC (e.g. front desk and manager's office), each PC
goes through the same setup steps above independently. All devices sync to the
same cloud account.

---

## Things That Still Need the Internet

A few features require going to the cloud version in a browser:

- Renewing your subscription
- Adding new staff members (the welcome email requires internet)
- Resetting a staff password by email
- Uploading your hotel logo

For staff password reset without email: the Super Admin can reset any
staff member's password directly from the **Staff** page in the offline app.

---

## Troubleshooting

**The app opens but gets stuck loading forever**

The `.env` file next to `RoomStatus.exe` may be missing or wrong.
Contact your account manager to get a fresh copy of the installer.

**Sync fails with "Invalid or expired sync signature"**

Your PC's clock may be wrong by more than 15 minutes. Fix it:
Windows → Settings → Time & Language → **Sync now**.
Then try syncing again.

**Sync fails with "Hotel is not registered for offline sync"**

Re-run the setup wizard. Close the app, delete the `database.db` file
that is next to `RoomStatus.exe`, then open the app again and go through
Step 4 above.

**A feature says "Not available offline"**

Some features (Paystack payments, smart lock credentials, Smart TV) require
the cloud. Log in to the cloud version in a browser to use them.

---

*MyRoomStatus — Offline Edition*

