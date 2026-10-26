# AdSense remediation — 2026-10-24

Revision: e663595dbd5a7b7ed593218d2146a7daa5072c5f
Pages run: https://github.com/chriscancod/clikey-chess/actions/runs/40096661221

Ad loading disabled across all routes; seven prerendered pages include original game guides, about, help/contact and privacy/storage. Existing public publisher variable is used only for the supported ownership meta tag. Tests: 12 pass; build and built-artifact checks pass. Local browser: guides render and legal e2→e4 move succeeds after hydration. No dependency added, no AdSense account setting changed and no review request submitted. Prepared from current production; original-checkout unrelated edits preserved. See docs/ADSENSE-FIXES.md for account-owner review steps and rollback notes.

VERIFIED: GitHub Pages build/deploy succeeded. All seven content routes, sitemap, robots and direct game return HTTP 200. Missing-route response is HTTP 404 with recovery content and noindex. Live HTML contains prerendered content and ownership meta tags; live entry bundle contains no ad loader. Browser verified the live chess guide. Evidence: docs/evidence/adsense-live-verification.json and docs/evidence/adsense-live-guide.png. Google review has not been requested; approval remains unverified.

---

# Composer-credit removal — 2026-10-22

Pushed revision: 3f98174ce39a40ea1541eb1bea3f540614a4a560
Pages run: https://github.com/chriscancod/clikey-chess/actions/runs/39793802581

Removed the composer attribution from the Clikey hub and rebuilt ONE MORE FLOOR browser pack. New content-addressed pack: index-d1a4e2366de6.pck. Prepared from current production in /tmp/clikey-credit-removal-20261022; unrelated original-checkout edits preserved. Production-checkout tests: 8 pass, 0 fail; Vite build passes. Native iPhone release was not uploaded. Latest check: GitHub workflow remains queued; no failure reported. The live game still served the previous pack at the verification attempt. Deployment completion and live credit removal are not yet verified.

---

# One More Floor shooting update — current deployment

Published revision: bbde6419ff65b3effae562e2fdd00638c76ead01
Pages run: https://github.com/chriscancod/clikey-chess/actions/runs/39427388777
Game: https://clikey.store/one-more-floor/index.html

Manual shooting, limited ammo, collectible ammo drops, emergency zero-ammo recovery and controller mappings are included. Hub control hints were updated. A content-addressed pack (index-47264cf91c87.pck) prevents browsers reusing the old gameplay pack. Deployment used the clean isolated production checkout; unrelated original-checkout edits were preserved.

Verified: Pages deployment succeeded; production site tests 8/8; Vite build; WebAssembly validation; root/hub/game HTTP200; live HTML and versioned pack match prepared files byte-for-byte. In the live browser, started a run, observed SHOOT and30/50, held F and observed27/50. Physical controllers and real-phone touch remain untested. Godot source tests and bot results are documented in the prior engineering session; no claim of a full live playthrough.

Local future exports use one-more-floor/tools/publish_web_to_hub.py to version the pack. No phone build was uploaded.

---

## Historical deployment report

# Clikey production deployment — 2026-10-17

Production repository: https://github.com/chriscancod/clikey-chess
Domain: https://clikey.store/
Hub route: https://clikey.store/hub/
Browser castle: https://clikey.store/one-more-floor/index.html

Published revision: ff173066e1f8e2981f869b42279cb9a023df964a
Pages run: https://github.com/chriscancod/clikey-chess/actions/runs/39068060722

The deployment was prepared from production revision ac0e4ff in an isolated checkout at /tmp/clikey-production-1uts0cla. It preserves CNAME, ads.txt and the existing GitHub Pages workflow. Unrelated untracked 3D-print files were not published. This original checkout's uncommitted work was left in place; fetch and compare origin/main before making future commits or pushes. Do not reset or discard the user's edits.

## AdSense setup remaining
Publisher verification is configured from the existing repository variable and public ads.txt. The selection screen has a display-ad placement, which is removed when a game is opened through the hub. No manual display ad is requested without a valid web slot ID. No placeholder ad is shown to players.

The user has not created an AdSense display ad unit yet. In AdSense: Ads > By ad unit > Display ads > Responsive > Save and get code. Name it Clikey Games Hub. Supply its numeric data-ad-slot value; do not use native AdMob unit IDs. Then set the VITE_ADSENSE_SLOT_ID repository variable and rerun the Pages workflow. Site approval, Privacy & messaging consent configuration, ad fill and any account-level Auto ads remain controlled by the user's AdSense account.

## Verified live
GitHub Actions build and deploy both completed successfully. The root, /hub/, manifest, browser game and ads.txt return HTTP 200. The live bundle includes the castle UI and configured AdSense publisher. Published index.pck and index.wasm SHA-256 values match the tested local production build. Display ads remain pending the missing web ad-slot ID.
