# Family Week

A shared week planner for Luke, Ellie and Frey. Each day has Morning, Afternoon and Evening slots, each slot holds up to 3 events, and each event is assigned to 1–3 people. Hosted on GitHub Pages, with events stored in Firebase (project `family-week-b2b64`).

## Files

- `index.html` – the whole app
- `firestore.rules` – database security rules (paste into Firebase)
- `manifest.webmanifest`, `icon-*.png`, `apple-touch-icon.png` – home-screen app icon and name

## One-time setup

1. **Security rules.** In the Firebase console, open Firestore Database → Rules, replace everything with the contents of `firestore.rules`, and click Publish.
2. **GitHub Pages.** In this repository go to Settings → Pages. Under "Build and deployment" choose *Deploy from a branch*, branch `main`, folder `/ (root)`, and Save. After a minute the site is live at `https://<your-github-username>.github.io/family-week/`.
3. **Allow sign-in from that address.** In the Firebase console, open Authentication → Settings → Authorized domains → Add domain, and enter `<your-github-username>.github.io`.
4. **Add to home screen.** Open the site on each phone, sign in with Google, then use Share → Add to Home Screen (iPhone) or ⋮ → Add to Home screen (Android).

## Adding Ellie

Her Google address needs adding in two places:

1. `firestore.rules`: add it to the list in `isFamily()`, e.g. `['lbailey211@gmail.com', 'ellie@example.com']`, then publish the rules again in Firebase.
2. `index.html`: add it to the `ALLOWED` list near the bottom.

## Notes

- The Firebase config in `index.html` is not a secret; access is controlled by the security rules, which only admit the listed Google accounts.
- Events are cached on each phone, so the calendar loads instantly and shows the last-known state if you're offline.
