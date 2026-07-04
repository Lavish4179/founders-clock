# Founder's Clock
Track the day you started a project - and see how many days you have been building 

A single-file day counter for anyone building something long-term. You set the
day you started; the app shows you how many days you've been at it, breaks that
down into years / months / weeks / hours, and tracks your progress toward
milestones — all the way to day 10,000.

Built by the founder of a cybersecurity advisory firm to count the days since
the company became real. Shared here free and open source in case it's useful
to anyone else chasing a long goal.

## What it looks like

A dark, industrial "mission clock": mechanical odometer digits roll up to your
current day count, with a milestone ladder (100 days, one year, 1,000 days,
five years, 10,000 days) and a progress bar toward whichever milestone is next.

## Install (Android)

The whole app is one HTML file. No app store, no account, no build step.

**Easiest (installable, works offline after first load):**
1. Open the hosted page in Chrome: `https://lavish4179.github.io/founders-clock/`
2. Tap the three-dot menu → **Add to Home screen**
3. Launch it from your home screen like any app

**Fully local (no hosting at all):**
1. Download `index.html` to your phone
2. Open it with Firefox and use its **Add to Home screen**, or use a
   shortcut-maker app to pin it. (Chrome hides "Add to Home screen" for
   `file:///` pages.)

Your start date is saved in your own browser's localStorage. Changing it is a
tap on "Change start date" at the bottom.

## Security posture

This project invites security review — issues and pull requests are welcome.
Here is what the app does and does not do, so reviews have a baseline to
verify against:

- **No data collection.** There is no server, no analytics, no telemetry, no
  cookies, and no form submission. Nothing you enter ever leaves your device.
- **One piece of stored data.** Your chosen start date (a `YYYY-MM-DD` string)
  is kept in your own browser's localStorage and validated on read and write.
- **One third-party request.** The page loads two typefaces from Google Fonts
  (`fonts.googleapis.com` / `fonts.gstatic.com`). Like any web request, that
  means Google's servers see the requesting IP address. No other network
  activity occurs, and the app functions (with fallback fonts) if the request
  fails or is blocked.
- **Locked-down CSP.** A Content-Security-Policy meta tag sets
  `default-src 'none'` and `connect-src 'none'`, allowing only inline
  styles/scripts and the two font origins. Even if hostile code were somehow
  injected, it would have no permitted network destination.
- **No `innerHTML` with dynamic data.** All dynamic values are inserted via
  `textContent` / DOM construction.
- **No dependencies.** No frameworks, no npm packages, no external scripts.
  The entire codebase is one readable HTML file (~400 lines).

If you find a weakness in any of the claims above, please open an issue — or
a pull request with the fix. Hardening suggestions that don't change the user
experience are especially welcome.

## Customizing

- **Start date:** defaults are set near the top of the `<script>` block
  (`DEFAULT_START`) — change it to your own day zero, or just use the
  in-app "Change start date" button.
- **Milestones:** edit the `MILESTONES` array to add your own targets.

## License

MIT — see [LICENSE](LICENSE). Use it, fork it, rebrand it for your own build.
