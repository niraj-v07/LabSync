# LabSync

**Find a free lab, request a slot, get it approved.**

LabSync is a web app that helps college students find and book free lab slots, and helps lab in-charges manage those requests in one place.

**Live site:** https://mylabsync.vercel.app

## The problem

Finding a free lab in college is a daily struggle. Students walk to a lab only to find it full, locked, or half out of order. Lab in-charges handle requests through verbal asks and scattered messages, with no clear way to decide who needs the lab most.

## Features

**For students**
- See all labs with their resources and live status (Free, Busy, Under maintenance)
- Request a lab slot by choosing a date, a time slot, a priority, and a reason
- Labs under maintenance can't be booked
- Track requests live (Pending, Approved, Rejected)

**For lab in-charges**
- Add labs, list their resources, and update their status
- See booking requests sorted by priority (High, then Medium, then Low)
- Approve or reject requests
- Double booking protection: the same lab, date, and slot can't be approved twice

Changes sync live between the two views, so there's no need to refresh.

## Demo logins

| Role | Email | Password |
|------|-------|----------|
| Student | student@labsync.com | student123 |
| Lab In-charge | incharge@labsync.com | staff123 |

On the login page, choose the role that matches the account.

## Tech stack

- HTML, CSS, and JavaScript (no framework)
- Firebase Firestore for the shared, real-time database
- Vercel for hosting

## Project structure

```
index.html    Login page
student.html  Student view: labs, booking form, my requests
staff.html    Lab in-charge view: requests, add and manage labs
logo.png
favicon.png
```

Each page contains its own styles and scripts.

## How it works

- Labs and booking requests are stored in two Firestore collections: `labs` and `bookings`.
- Both pages use Firestore's real-time listeners (`onSnapshot`), so an update from staff appears on the student page immediately, and the other way around.
- Login checks the demo accounts in the page script, and the logged-in role is kept in the browser's `localStorage` to guard the pages.

## Limitations

This is a hackathon project, so some parts are simplified:
- **Demo logins only.** There is no real authentication, and the accounts are hardcoded.
- **Open database rules.** The Firestore rules for `labs` and `bookings` are open for the demo, so don't store real student data.
- No notifications yet, and no usage reports.

## What's next

- Firebase Authentication with real student and staff accounts
- Role-based Firestore security rules
- Email or phone notifications when a request is approved
- Usage reports for lab in-charges
- Support for multiple departments

## Built for

[BuildyourOwnWebsite Hackathon](https://buildyourownwebsite.devpost.com/) by Roxten Studios.

## AI disclosure

The idea, features, and project direction are mine. I used AI heavily for the design and for writing some of the code, and I set up, tested, and deployed the project myself (Firebase, GitHub, Vercel).
