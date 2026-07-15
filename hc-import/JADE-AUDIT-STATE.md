# Jade Mockup ↔ Live Audit — Execution State (resume doc)

## ✅ AUDIT COMPLETE (2026-07-13)
All 47 Jade articles verified 1-by-1 against live. Every genuinely-broken item fixed.
FINAL SCOPE DECISION (Brady, 2026-07-13): third-party app articles SHIP AS-IS matching live.
The live site does NOT put third-party mobile screenshots in iPhone bezels — it shows raw
2-up composites with soft shadows. Framing them would DIVERGE from live, so we do not.
(connect-jade framing was correct because those were Blockstream app screens with no live
equivalent; third-party articles already embed the exact live CDN images inline → match.)
Nothing further to build. Deploy live at commit f20db1c, Pages build `built`.
See "Session close-out" at bottom for the full done-list.


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
- Cat B (ff56567): use-jade-as-a-stateless-signing-device — 8 transparent Jade screens, 2 sub-procedures.
- Cat B (fabb450): access-jade-plus-air-gapped-with-seedqr — 5 transparent Jade screens.
- Polish small (374ec93): migrate, supported-air-gapped-functionality-via-qr, -via-jadelink, dice — inline GCS -> transparent framed.
- (9f8549c) air-gapped-jade-plus-setup — 11 Jade screens, render-verified.
- (8dcb151) verify-receive-addresses — 3 Jade transparent + 1 Sparrow desktop RAW (desktop-as-rectangle default applied).
- (8e0039d) access-jade-air-gapped-with-qr-pin-unlock — 7 screens.
- (b5a5704) jade-overview — added Uninitialized + Active status screens.
- TOTAL BUILT: 14 articles.

## RESOLUTION MAP (as of 14 built)
KEEP-AS-IS verdicts (no build; already correct/good or type-exception):
- Cat F (mockup adds Jade-screen value over TEXT-ONLY live -> KEEP): restore-recovery-phrase, use-jade-as-a-2fa, disable-bluetooth, fix-issues-pairing-bluetooth, which-xpub-export.
- Already-good polished composites (keep-better): bip85 (my Options-header fix 429-7547 is BETTER than live's outdated Wallet header), enable-a-duress-pin, perform-a-factory-reset, what-is-the-wallet-id, add-jade-plus-to-an-air-gap-supported-app, send-air-gapped-bitcoin-transactions-via-qr (471-27/28 good).
- Type-exception (already show correct images inline matching live; grids/desktop/diagrams/icons can't/shouldn't be bezel-framed -> KEEP raw): create-a-seedqr (SeedQR grids), calculate-the-final-word (grids), how-do-i-set-up-a-wallet-erase-pin (grids), use-jade-with-electrum (desktop), use-jade-with-sparrow (desktop), blockstream-jade-quickstart-guide-for-desktop (desktop), how-does-jade-protect...blind-oracle (diagram), what-is-a-seedqr (diagram), blockstream-jade-vs-blockstream-app (diagrams), best-platforms (icons), use-jade-as-a-bitcoin-miner (grid+desktop).

## GENUINE REMAINING BUILDS (mixed: polish Jade parts transparent, keep desktop/photo raw; or fingerprint/3rd-party)
- perform-an-air-gapped-firmware-upgrade (Jade parts + photo), send-air-gapped-bitcoin-transactions-via-jadelink (JadeLink+Jade), back-up-a-multisig-configuration-on-jade (Jade + diagram), set-up-a-personal-blind-oracle-with-umbrel (Jade + Umbrel photos).
- FINGERPRINT (need current top-right source from Main User Flows + text lower/bottom->top right): add-a-bip39-passphrase-for-jade; verify-your-recovery-phrase (mockup keep but under-imaged — decide).
- THIRD-PARTY (iPhone-frame mobile screenshots, desktop raw): use-jade-plus-qr-scan-with-nunchuk, use-jade-with-nunchuk-honey-badger-wallet, use-jade-plus-qr-scan-with-bluewallet, use-jade-plus-qr-scan-with-specter, use-jade-qr-scan-with-sparrow.
- QUICKSTART mixed (mobile app + Jade + SeedQR): blockstream-jade-quickstart-guide-for-ios, -android. DEFAULTS in use (Brady "continue"): polish transparent; keep top-right fingerprint (don't use outdated bottom-right live imgs); desktop screenshots kept RAW on white (don't transparent-ize); keep-better on already-good polished composites; 3rd-party mobile -> iPhone bezel.
- REMAINING notable: air-gapped-setup(11 imgs incl SeedQR-grid composite), qr-pin-unlock(4 jade+3 QR-scan photos), fingerprint articles (verify-recovery, bip39 — need current top-right source from Main User Flows, and change text lower/bottom->top right), desktop-screenshot articles (electrum, sparrow, quickstart-desktop, add-jade-plus, send-airgap-qr — keep desktop raw), third-party (nunchuk/specter/bluewallet/honey-badger/sparrow-qr — big), SeedQR-grid articles (create-seedqr, seedqr-vs-qrpin, calculate, wallet-erase-pin — grids don't transparent-ize well, keep on white or handle). Already-good/keep: bip85(my fixed 429-7547), duress, factory-reset, wallet-id, send-airgap-qr(471-27/28).

## NEXT (resume here)
Continue Cat B clean pure-Jade-landscape articles (polished transparent imgs already in /tmp/polished/): bip39(5), bip85(4), access-seedqr(5), add-jade-plus-airgap(4+1), verify-receive-addr(3+1), send-airgap-qr(done? 5), duress(3), calculate(4 SeedQR-grid), wallet-erase-pin(6 SeedQR-grid), air-gapped-setup(11), qr-pin-unlock(4jade+3 photos). For each: verify polished imgs (spot-check non-1400x500 for transparent-ize damage per PITFALL), copy to _staging, restructure HTML to live section/step order, verify, commit. verify-recovery: use CURRENT top-right-fingerprint Jade screen (live img outdated) — may need Main User Flows source. Then Cat D third-party (frame portraits iPhone), then Cat F judge keep/remove.
NOTE: /tmp/polished landscape imgs are transparent-ized; RE-VERIFY any that were full-bg screenshots (desktop app etc.) were not damaged before using.

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

## LIVE CRAFT PUBLISH — Set Up/Transact/Recover section (2026-07-13)
Craft entry IDs (site=help, section helpCenterProductsStructure, source UID f0618608-a1cf-4ec4-9ce6-f7e7d6798504):
- jade-overview 198 | set-up-jade 522 | download-a-companion-app-for-jade 340 | connect-jade-to-a-companion-app 662
- perform-a-genuine-check-with-jade 1090 | receive-bitcoin-using-jade 786 | send-bitcoin-using-jade 859
- set-up-watch-only-access-for-jade 1164 | verify-your-recovery-phrase 976 | restore-recovery-phrase-to-jade 1040
- migrate-to-jade-from-another-hardware-wallet 1144 | update-jade-firmware 436

PUBLISH METHOD (proven): navigate entry → read live CKEditor getData() (source of truth) → surgical DOM edit (remove old <img>/<figure>, insert grouped composite <figure class="image"><img src="https://btin-dev.github.io/dobby-assets/hc-import/_staging/NAME.png?v=N"> at image-before-step anchors, preserving ALL live text + Craft entry-ref links) → editor.setData + updateSourceElement → FormData(form) with draftId/provisional deleted, action=elements/save → Craft.sendActionRequest POST → reload entry, verify canonical (!draftId && elementId===canonicalId) + new refs present + no dxp-staging → curl bare public URL (~60s ISR propagation).

PUBLISHED (all 9 image articles, canonical+public verified):
- connect-jade 662: 7 individual → 3 grouped (connectjade-appgroup-1, connectjade-3, connectjade-appgroup-2)
- receive 786: 5 → rcv-appgroup-1, rcv-4, rcv-solo-5
- send 859: 5 → snd-appgroup-1, snd-5 (+ fixed duplicate step "4."→"5.")
- genuine-check 1090: 3 → gc-appgroup-1 (inside the Note blockquote wrapper)
- jade-overview 198: kept hardware diagram (still dxp-staging 41927032727193, loads OK publicly), upgraded 2 status screens → jov-2, jov-3
- set-up-jade 522: 6 → 468-3 (steps1-3), 468-4 (steps4-5)
- restore 1040: was image-less → added 471-9 (step1), 471-10 (step3)
- migrate 1144: 1 → mig-1 (+ fixed 4x "seed phrase"→"recovery phrase")
- verify-your-recovery-phrase 976: 6 → verify-1 (steps1-3), verify-2 (steps4-6). REBUILT from the live article's 5 actual screens (01-05) since the old mockup 471-6/471-7 dropped select-length + select-connection and had wrong word-entry screens. CAVEAT: verify screens show fingerprint bottom-right (older firmware) — flagged to Brady, he approved publishing anyway.

TEXT-ONLY (no live images, nothing to publish): download-companion 340, watch-only 1164, update-firmware 436.

KEY LEARNINGS: (a) surgical image-swap preserving live text+links is the safe pattern (mockup text was byte-identical to live for the app-flow articles). (b) Jade-DEVICE-screen articles: VERIFY the mockup composites contain ALL live screens before replacing (set-up-jade's 468-3/468-4 covered all 6; verify's 471-6/471-7 dropped 2 → had to rebuild). (c) elements/save canonical path never silently failed here; every reload verified canonical=true. (d) CDN edges serve stale transiently — a single "MISS" on public poll isn't a real failure; check the actual served image srcs.
