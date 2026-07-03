# Jade Mockup ↔ Live Audit — Execution State (resume doc)

Working file: `hc-full-mockup.html` (repo btin-dev/dobby-assets, GitHub Pages).
Live articles: `help.blockstream.com/blockstream-jade/<section>/<slug>`.

## Guiding principle (from Brady)
Per-article JUDGMENT, not blind live-mirroring:
- Keep the mockup where it's as-good-or-better than the live.
- Fill genuine gaps from the live (missing/wrong/app-vs-Jade).
- PRESERVE prior corrections (e.g. terminology, orphan fixes).
- Report the judgment calls at the end (esp. Cat F keep/remove).

## Pipeline (proven on connect-jade + Cat A)
1. curl live page → ordered gcs image URLs (SSR has them).
2. Download (already done: /tmp/jade-live/<slug>/NN.png).
3. Classify: portrait(app/3rd-party)=iPhone bezel; landscape(Jade device, already framed by live)=transparent-ize; diagram/QR/icon=as-is.
4. iPhone framing: clone Figma template phone 420:3983 (page 426:4133), REDLAYER=420:4060, set fills to uploaded hashes, arrange row, group, export scale 2, split by connected components, clean gray (#f5f5f5 flood from border), transparent.
5. Transparent-ize Jade landscape: connected-component flood remove #f5f5f5/white.
6. Restructure HTML: one figure per step in live order. `<figure class="image staged"><img src="_staging/NAME-N.png?v=27"></figure>`. Re-serialize ART via JSON.stringify; verify only intended slugs changed.
7. Verify via Brave headless render (NO live browser loop). Deploy at END (one Pages build — Pages hangs repeatedly; re-POST build to unstick).

## Figma
- Whitelisted write file: rG61aDakwvljctiEL1dodn (Claude workspace). Jade staging page = 426:4133.
- iPhone template phone: 420:3983 (467x815), REDLAYER 420:4060 (368x796 FILL). App page 233:604 has 1/2/3/4-phone templates.
- Main User Flows (READ ONLY): S48afnoEiPvsniJBe33T0v, page 0:1 "Jade Plus - Flows" (real Jade screens if needed).
- Upload: upload_assets(count) → POST files (use PYTHON not bash arrays — bash misaligns) → get hashes → use_figma set fills (upload nodeId does NOT bind).
- Clean up temp groups after export (g.remove()).

## Data on disk
- /tmp/jade-articles.json — 72 slugs + live URLs + mockup img counts.
- /tmp/jade-audit-results.json — per-article live app/jade/other counts.
- /tmp/jade-live/<slug>/ — all downloaded live images (47 folders).
- /tmp/parse-hc-lib.js — HC/ART parser.

## DONE (committed)
- connect-jade (df81f2b + earlier) — 6 app iPhone + 1 Jade, matches live. [Pages build was hanging]
- Cat A (5c1687d): receive-bitcoin, send-bitcoin, perform-a-genuine-check — app screenshots framed, per-step, verified.

## REMAINING (apply the principle)
- **enable-swaps** — live has pre-composed app+Jade PAIR images (3000x2416) + 2 app portraits. Special handling.
- **Cat B (judge; many may be adequate)**: jade-overview(overview not procedure), verify-your-recovery-phrase(FLAG below), use-jade-as-a-stateless-signing-device(8), how-do-i-set-up-a-wallet-erase-pin(6), access-jade-air-gapped-with-qr-pin-unlock(7 incl QR photos), add-a-bip39-passphrase-for-jade(5), calculate-the-final-word(4 SeedQR grids), access-jade-plus-air-gapped-with-seedqr(5), create-a-bip85-child-recovery-phrase(4), add-jade-plus-to-an-air-gap-supported-app(5), verify-receive-addresses-with-an-air-gapped-jade-plus(4).
- **Cat C (no mockup images — clear build)**: back-up-a-multisig-configuration-on-jade(8), create-a-seedqr-from-my-recovery-phrase(8), blockstream-jade-quickstart-guide-for-desktop(7), use-jade-with-electrum(7), perform-an-air-gapped-firmware-upgrade(6), send-air-gapped-bitcoin-transactions-via-jadelink(6), blockstream-jade-quickstart-guide-for-android(6), use-jade-with-sparrow(5), set-up-a-personal-blind-oracle-with-umbrel(4), seedqr-vs-qr-pin-unlock(2), create-a-recovery-phrase-using-dice(2), use-jade-as-a-bitcoin-miner(2), supported-air-gapped-functionality-via-qr(1), supported-air-gapped-functionality-via-jadelink(1), what-is-a-seedqr(1), how-does-jade-protect-my-recovery-phrase-with-a-blind-oracle(1 diagram).
- **Cat D+E (third-party/diagram)**: use-jade-plus-qr-scan-with-nunchuk(20), use-jade-with-nunchuk-honey-badger-wallet(20), use-jade-plus-qr-scan-with-bluewallet(17), use-jade-plus-qr-scan-with-specter(13), use-jade-qr-scan-with-sparrow(13), best-platforms-for-jade-plus-qr-scan(4 icons), blockstream-jade-vs-blockstream-app(6 diagrams), blockstream-jade-quickstart-guide-for-ios(mixed). Brady: replicate full set incl SeedQR + 3rd-party app screenshots framed in iPhone bezels.
- **Cat F (judge keep/remove; live text-only)**: restore-recovery-phrase-to-jade(mockup 5), use-jade-as-a-2fa-authentication-device(4), disable-bluetooth(3), fix-issues-pairing-jade-via-bluetooth(2).

## BRADY DECISIONS (2026-07-03)
- POLISH EVERYTHING to transparent bezels: ALL ~40 Jade articles get the polished treatment (Jade landscape = transparent-ize white bg; app/3rd-party portrait = iPhone bezel; SeedQR/diagram = transparent/as-is). Replace raw inline-GCS images too.
- Fingerprint verify-recovery = KEEP "top right" (current Jade firmware shows it top-right; the LIVE image showing bottom-right is OUTDATED). KEY INSIGHT: live images can be stale; where they are, mockup should reflect CURRENT Jade — source current screens from Main User Flows (S48afnoEiPvsniJBe33T0v) rather than the outdated live GCS image. For verify-recovery specifically, use a current top-right-fingerprint Jade home/Active screen.
- Re-audit (all imgs, not just _staging): ~20 articles already show live's exact images inline (matched count) but as RAW white-bg — these still need polishing per Brady. Genuinely under-imaged (add screens): verify-recovery, air-gapped-setup(5/11), qr-pin-unlock(4/7), stateless(4/8), wallet-erase-pin(4/6), bip39(3/5), bip85(3/4), calculate(2/4), seedqr-access(3/5), add-jade-plus-airgap(4/5), verify-receive-addr(3/4), jade-overview(2/3), enable-swaps. Third-party big: nunchuk(20), specter(13), bluewallet(17), honey-badger(20), sparrow-qr(13).

## PITFALL (critical, learned 2026-07-03)
Blanket transparent-ize (flood-remove border white/#f5f5f5) is CORRECT only for Jade-device-on-white-margin composites (1400x500 etc: dark device, white margin → transparent margin, keep device). It DAMAGES full-background content images: desktop app screenshots (Electrum/Sparrow 3744x2016 — white UI bg gets eaten/hollowed), and can over-strip diagrams. The /tmp/polished set (251 imgs) is NOT trustworthy as-is — regenerate with per-type logic:
- Jade device composite (mostly-white image w/ a compact dark device) → transparent-ize (remove white margin).
- Full-bg screenshot (content fills frame, e.g. desktop app, mobile app UI) → DO NOT transparent-ize; keep on white OR frame in a device bezel (iPhone for mobile app portrait; leave desktop screenshots as clean rectangles, maybe on a subtle card).
- SeedQR grid / QR / diagram → keep as-is (check per case).
Detection heuristic: after border-flood, if remaining opaque area is a SMALL fraction (compact device on white) → transparent-ize OK; if border-flood would clear a LARGE fraction (content is white-bg) → keep original.
Portraits needing iPhone framing (from /tmp/portraits/list.json): only 5 (enable-swaps x2, quickstart-ios x1, nunchuk x1, honey-badger x1). Most 3rd-party mobile screenshots are near-square (2250x2232) or landscape → not caught as portrait; decide framing per Brady ("iPhone bezel the 3rd-party app screenshots").

## FLAGS for Brady (report at end)
1. verify-your-recovery-phrase: live shows 8-char fingerprint BOTTOM-right (matches live text "bottom right"). Earlier this session Dobby changed the mockup text to "top right" per Brady — that edit may have been WRONG (the top-right F6B624 is the wallet ID on a different screen). NEEDS Brady's call: revert to "bottom right"?
2. Cat F verdicts (keep/remove) — pending per-article judgment.
