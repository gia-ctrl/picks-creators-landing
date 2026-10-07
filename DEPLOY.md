# GetPicks Creators landing: deploy brief (for the Claude agent)

## What's here
- `index.html`: the whole page in ONE file. Fonts, images and the runtime are all inlined, so there are no external dependencies besides Google Fonts. Open it locally to preview.
- `vercel.json`: a minimal static config.

## Deploy (Vercel)
1. Create a new Vercel project and choose **Other / static**. There's no build step.
2. Upload this folder (or push it to a repo). The output directory is the root.
3. Point the domain, e.g. `creators.getpicks.app`.

## Before going live (required)
1. **Formspree:** create a form at formspree.io and copy its id.
   In `index.html`, search for `https://formspree.io/f/NEW_ID` and replace `NEW_ID`.
   The form POSTs JSON: `name, email, x_handle, followers, paid_channel, source, _subject`.
   - Success shows the "You're in line" state.
   - Failure shows an inline error, and the user can retry.
2. **Scarcity numbers:** set the real values. Search for `spotsTotal` / `spotsLeft`. The defaults are 50 and 17 and **must be true** (FTC: no fake scarcity).
3. **Illustrative data:** the creator card (@marcus), the leaderboard and the earnings numbers are examples. Either label them "Illustrative" or swap in real, consented creators.
4. **Legal review:** "Withdrawals… fastest", the earnings figures, and the founding perks (badge, top tier, launch-day feature) must match what we actually offer.

## Tracking (recommended for the paid-social test)
Add before `</head>`:
- Meta Pixel `PageView`, plus a `Lead` event on successful submit. Hook it into the `.then` of the fetch in the submit handler; search for `FORM_ENDPOINT`.
- GA4 or Plausible if you want.
- Keep the UTM params: Formspree stores the referrer automatically. If you need UTMs in the submission, add `utm: location.search` to the JSON body.

## Notes
- The page is responsive; check it at 375px, 768px and 1280px.
- Editing the page: change the source `Picks Creators Landing v3.dc.html` in the design project and re-export. Don't hand-edit the bundled `index.html` beyond the endpoint and the numbers.
