# Medical Info Sheet

A free phone app by Cygnus Solutions that holds the medical history of each family member. Open a person's page and hand the phone to the doctor so the history is complete before the exam starts.

Open it at https://cygnus-solutions.github.io/Medical-Info/ and press Install in the top bar to put it on your home screen. On iPhone, tap Install to see the Add to Home Screen steps.

## What it does

- One page per family member, laid out in the order a doctor takes a history: allergies and alerts first, then medicines, conditions, surgeries, usual condition, contacts, IDs and documents.
- Each section shows the date it was last updated and turns amber after 6 months. Press Still correct in the editor when nothing has changed.
- Taken now beside each medicine records the time of the last dose.
- The PIN locks editing, IDs and documents. The medical summary opens without it since the doctor needs it in an emergency.
- Every QR starts with the time it was made and the date the info was last changed, so whoever scans it knows how old it is.
- Share has three tabs:
  - **For the doctor.** The full history as formatted text, split into parts when it is long. The doctor scans each part with the phone camera and copies the text into the chart.
  - **Family sync.** A moving QR that holds the whole page. On the other phone, press Scan on the home screen. When the two phones disagree, a review screen shows both values with the newer one picked, and you choose which to keep. Photos and documents are left out of the code since they are too large for it.
  - **Wallet card.** A fold-over card with a summary on the front and a QR on the back, plus a full printed sheet.
- Blood pressure and blood sugar logs take a reading in a few taps from the summary. The summary shows the latest reading, the 7-day average, a 30-day chart and flags readings outside the usual limits, and the doctor's text and printed sheet carry the readings too.
- Vaccines are logged one shot at a time with the date, lot number, where it was given and when the next shot is due. Add next shot copies the vaccine for the following dose or booster, and the home screen flags a vaccine that is due within 30 days or overdue.
- The app is in English and Thai. Pick the app's language at the bottom of the home screen or in Settings. The summary has its own switch for the language the doctor reads, which also sets the doctor's QR text, the wallet card and the printed sheet. What the family typed stays as they wrote it, and choices like allergy severity or dose show in the doctor's language. Thai dates use the Buddhist year.
- Settings has Export and Import for a full backup file with photos and documents. Importing keeps whichever copy of each person was changed last.

## Files

- `index.html` holds the whole app, including the QR generator (qrcode-generator by Kazuhiko Arase, MIT licence).
- `vendor/jsQR.min.js` reads QR codes from the camera on phones whose browser has no built-in reader (jsQR by Cosmo Wolfe, Apache 2.0 licence).
- `sw.js` keeps the app working offline. Change `CACHE` to a new version on every update so phones load the new files.
- `manifest.webmanifest` and `icons/` let it install to the home screen. The Install button shows when the browser offers installing, and on iPhone it shows the Add to Home Screen steps.
- `i18n/th.js` holds the Thai text. Each line maps the English in `index.html` to Thai. To add a language, copy it, translate the right-hand side, load it in the head of `index.html` and add it to `LANGS`.
- `icons/cygnus-swan.svg` is the Cygnus Solutions swan used in the top bar, the credit line and Settings.
- `vendor/fonts/` holds Cinzel for the Cygnus wordmark (SIL Open Font License, in `Cinzel-OFL.txt`).

## Where the data lives

Everything stays in the browser storage of the phone it was entered on. Clearing the browser data or uninstalling the app deletes it, so export a backup after big changes. The PIN hides screens and does not encrypt the data.

## Hosting

It has to be served over https to install and work offline, so it is hosted on GitHub Pages from the `main` branch of cygnus-solutions/Medical-Info. Opening `index.html` straight from a folder works for a look but will not install.

## Made by

Cygnus Solutions. The credit shows on the home screen, in Settings, on the back of the wallet card and at the foot of the printed sheet.
