# Frown Face-Off

A tiny static site: friends open a link, take a webcam frown (one per hour), and vote. No accounts. Shared data lives in a free Firebase Realtime Database.

## Setup (about 5 minutes)

1. **Create the database.** At https://console.firebase.google.com click *Add project* (skip Analytics), then *Build -> Realtime Database -> Create database* (any region, start in **locked mode**).
2. **Copy the URL.** At the top of the Data tab is a URL like `https://xxxx-default-rtdb.firebaseio.com`. Paste it into `firebase-config.js`.
3. **Paste the rules.** In the Realtime Database *Rules* tab, replace everything with the contents of `database.rules.json` and click *Publish*. These rules only allow current-hour frowns, block overwriting or deleting them, and cap name and photo size.
4. **Host it.** Push these files to a GitHub repo, then *Settings -> Pages -> Deploy from branch -> main / root*. Share the `https://<you>.github.io/<repo>/` link.

## Notes

- Each browser gets a random anonymous ID, so "one per hour" is per browser, not per person. Anyone with the link can play; share it with friends only.
- To remove a bad entry, delete it in the Firebase console Data tab.
- Rounds are clock hours (UTC-based). Data older than 72 hours stops showing.
