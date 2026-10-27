# Simczech Pitaya: scenarios

Twelve mechanisms fixed before the polls open, for comparison with the official count. These are **scenarios, not forecasts**: no probabilities, no contribution to the Original. Baseline: the sealed v2 Original, version `2026-10-27_0146`, from [prediction.json](../../prediction/2026-10-27_0146/prediction.json) and [sectors.csv](../../prediction/2026-10-27_0146/sectors.csv). All inputs were read offline. The timestamp of this build is in [scenarios.json](scenarios.json).

**Publication status:** prepared and checked locally. `SHA256SUMS` is a local fingerprint, not an independent timestamp or evidence of publication. This work order forbids network access and writes outside this folder, so external sealing and publication are still required. The PLAN calls for the fingerprint and timestamp proofs on the repository before 06:00 CET, the figures revealed there at 21:00 CET, and the scenario set on the page only after the count. No scenario figures should be published early.

Main-list columns below are seats. Signatures show **sealed baseline → scenario**; percentages are shares of all valid votes unless explicitly labelled turnout. The coalition always means the five government lists; Amcha is separate. The JSON contains all 15 shares and seats, every bloc, the largest lists, precise allocation inputs, source citations and further signatures.

| Scenario | Likud | Yashar | Together | Coalition | Main count signature: baseline → scenario |
|---|---:|---:|---:|---:|---|
| Original v2, reference | 23 | 22 | 15 | 52 | Coalition share 41.0%; Arab+Druze in-person proxy turnout 59.0%; effective Haredi turnout 79.7% |
| S1 · Channel 14 and Direct Polls are right | 30 | 21 | 12 | 60 | Likud 17.5 → 22.2%; coalition 41.0 → 46.3% |
| S2 · The other pollsters are right | 21 | 24 | 14 | 50 | Likud 17.5 → 15.6%; coalition 41.0 → 38.6% |
| S3 · Past poll errors recur | 25 | 20 | 14 | 55 | Shas+UTJ 12.1 → 13.5%; Reservists 2.4 → 0.96%; Amcha 2.2 → 0.0% |
| S4 · Arab turnout reaches the survey level | 23 | 22 | 15 | 52 | Arab+Druze in-person proxy turnout 59.0 → 63.0%; Ra'am+Joint List 11.3 → 11.9% |
| S5 · Arab turnout returns to the 2021 low | 24 | 22 | 16 | 54 | Arab+Druze in-person proxy turnout 59.0 → 44.6%; Ra'am+Joint List 11.3 → 9.2% |
| S6 · Haredi mobilisation weakens | 23 | 22 | 15 | 52 | Effective Haredi turnout 79.7 → 72.0%; Shas+UTJ 12.1 → 11.5% |
| S7 · The two leaders squeeze their camps | 29 | 29 | 12 | 52 | Likud+Yashar 34.1 → 44.1%; smaller right-camp lists 25.7 → 20.6% |
| S8 · Both small lists cross the threshold | 21 | 20 | 14 | 48 | Reservists 2.4 → 3.334%; Amcha 2.2 → 3.334%; each wins 4 seats |
| S9 · Yashar loses new-party enthusiasm | 24 | 19 | 16 | 53 | Yashar 16.6 → 14.5%; recipient lists together 42.3 → 44.4% |
| S10 · The voter archetypes are right | 25 | 14 | 26 | 51 | Together 11.7 → 19.9%; Yashar 16.6 → 11.1% |
| S11 · The social-media lean persists | 24 | 21 | 15 | 54 | Otzma 6.4 → 7.3%; Likud 17.5 → 18.3%; Yashar 16.6 → 16.0% |
| S12 · A 2015-style Likud surge | 32 | 19 | 13 | 57 | Likud 17.5 → 24.2%; Together+Yashar 28.3 → 24.8% |

Largest by seats: Yashar in S2, Together in S10, Likud and Yashar tied at 29 in S7, Likud in the other nine. Likud remains ahead on votes in S7. S8 has 48 coalition seats, 54 opposition, 14 Arab and 4 Amcha; coalition plus Amcha is 52. Amcha never silently enters the coalition definition.

The mechanisms and their sourced sizes are fixed as follows. CSV record numbers count the header as record 1. JSON citations identify exact fields; all citations also carry input fingerprints in `scenarios.json`.

| Scenario | Size and application | Saved source |
|---|---|---|
| S1 | Copy the complete conditional vector, equal weight to the two families' last polls. | [Loquat scenarios](../loquat/scenarios.json), `/b_government_close/shares_pct` |
| S2 | Copy the complete conditional vector, equal weight to the other six families' last polls. | [Loquat scenarios](../loquat/scenarios.json), `/c_other_pollsters/shares_pct` |
| S3 | Copy the private scenario unchanged; do not apply its corrections again to the Original. | [Pitaya](../pitaya/prediction.json), `/shares_pct`, verified against [the private 00:45 seal](../../prediction/2026-10-27_0045-pitaya/prediction.json), `/estimate/shares_pct` |
| S4 | Arab+Druze benchmark 63%; converted effective Arab row 71.213910%, from 66.8%. | [Turnout memo](../lucuma/memos/runs/turnout/memo.md), line 39, Statnet projection reported 21 October; definitions line 23; [2022 box sectors](../../data/clean/sectors_2022_box.csv), Arab, Druze, envelopes and TOTAL rows |
| S5 | Arab+Druze benchmark 44.6%; converted effective Arab row 50.993487%, from 66.8%. | [Turnout memo](../lucuma/memos/runs/turnout/memo.md), line 18, March 2021 row; same sector conversion inputs as S4 |
| S6 | Effective Haredi turnout 72%, a 7.7-point fall from 79.7%. | [Turnout memo](../lucuma/memos/runs/turnout/memo.md), line 77, Haredi forecast's 72–85% range; sealed sector table, Haredi row |
| S7 | April 2019 gains of 6.11 and 5.89 seats become +5.091667 and +4.908333 points, respectively; +10.0 points combined. | [Historical poll errors](../../analysis/poll_errors.csv), records 186–187, `2019a/final_mean/likud` and `main_challenger` |
| S8 | Each list reaches 143,666 / 4,309,270 = 3.333882% (3.334% in the saved results). | [Past results](../../data/clean/results_past.csv), record 37, `2019a/raam_balad`; minimum across passing lists in the 2015–2022 record at the current threshold |
| S9 | Seven cases' mean overrating +2.492857 seats becomes a Yashar loss of 2.077381 points. | [Historical poll errors](../../analysis/poll_errors.csv), records 165, 166, 316, 317, 318, 625, 626; [analysis section d](../../analysis/poll_errors.md) |
| S10 | Copy the complete Rambutan v2 national vector. | [Rambutan v2](../rambutan-v2/national.json), `/shares_unrounded_pct` |
| S11 | Add the saved corrected v1 moves once; their sum is −1.233 points, so normalize by 100/98.767. | [Carambola v1](../carambola/carambola.json), `/2026/moves_pts` |
| S12 | Likud's 30 result seats minus 22 final-poll seats gives +8 seats, converted to +6.666667 points. | [Historical poll errors](../../analysis/poll_errors.csv), record 16, `2015/final_mean/likud` |

Turnout needs a definition conversion. The sealed sectors are disjoint **ballot-box proxies**, not a census of individual ethnicity or religion. Arab excludes the separately classified Druze sector and includes qualifying boxes in mixed cities. Haredi includes qualifying boxes outside Haredi towns. Loquat assigns 2022 double-envelope ballots proportionally to each sector's registered voters; the resulting effective turnout includes these attributed ballots. The derivation is documented in [Loquat's sector layer](../loquat/README.md) and `effective_sectors` in [run_model.py](../loquat/run_model.py).

That neutral envelope contribution is `e = 100 × 462807 / 6788804 = 6.817209629` turnout points. Keep it fixed for the conversion, along with the 2022 proxy electorate: `R_A = 933957`, `R_D = 92402`. Druze effective turnout stays at the sealed 55.7%, implying an in-person rate of 48.882790371%. For a combined Arab+Druze in-person benchmark `T`, set only the effective Arab row to:

`t_A = [T × (R_A + R_D) − R_D × (55.7 − e)] / R_A + e`.

The baseline on that combined in-person basis is 58.983469%; the target levels are 63.0% and 44.6%. These imply effective Arab turnout of 71.213910% and 50.993487%. The memo's Arab/Druze locality measure excludes mixed-city residents; our proxy includes some mixed-city boxes. Statnet's precise denominator is undisclosed. Thus this is an explicit scenario mapping, not a proven survey-to-proxy calibration. The Original already applied Statnet's **63−56 = 7-point increase** to its Arab proxy. S4 tests taking the **63% level** on the memo's stated combined definition; it does not introduce a second independent survey observation.

For S4, S5 and S6, the changed sector's mass is `old_weight × new_turnout / old_turnout`. Leave the other three masses and all within-sector list shares fixed, normalize the four masses, then sum the sector rows. This holds registered electorate and valid-ballot rates fixed. The exported sector rows reproduce the Original after balanced rounding, though before rounding their aggregate differs by up to 0.045362 points per list. These scenarios use the exported rows directly, without an extra national adjustment. Their changed weights are saved in the JSON.

For S6 I used the work order's permitted **72% turnout-memo low end**, directly on the effective Haredi proxy. It is a subjective community estimate with imperfect geographic coverage, not an empirical turnout percentile. The largest combined Haredi seat miss in the analysis was an **underestimate** of 4.33 seats in April 2019, so treating its magnitude as abstention would require reversing the sign and assuming a seat-to-turnout relationship. The memo gives a more direct turnout scenario. With the fixed envelope contribution, S6 implies in-person Haredi proxy turnout 72.882790 → 65.182790%.

S7, S9 and S12 convert seat errors using **100/120 points per seat**, matching the existing private scenario's convention. This is a seat-equivalent stress size, not a measured historical valid-vote error: thresholds and surplus allocations make those different. No historical result share is subtracted from a poll seat percentage. S7 preserves the historical split of the combined gain between the two leaders, rather than inventing an equal split.

“Own camp” for Likud's transfers includes Shas, UTJ, Religious Zionism–Zehut, Otzma and Amcha. Amcha remains outside the reported coalition. Haredi Public and aggregate `other` are excluded from donor pools; the latter cannot isolate Noam. S7's Yashar donors are Together, Democrats, Yisrael Beiteinu and Reservists. S8's Reservists donors are the other four opposition lists; Amcha's donors are the five government lists. S12 uses one donor pool comprising Likud's five smaller camp lists plus Together and Yashar. Every donor contributes in proportion to its sealed baseline share.

S9 averages all **seven brand-new-party cases**, equally by case: Kulanu, Yachad, New Right, Zehut, Gesher, New Hope and New Economic. Errors are −1.23, +4.15, +6.11, +5.56, 0, +2.86 and 0 seats. This includes the two zero-poll cases and Kulanu's under-polling, excludes new alliances and “first separate run,” and differs from the private scenario's equal-election averaging. The Yashar loss goes only to Together, Democrats, Yisrael Beiteinu and Likud, in proportion to their baseline shares.

Allocation uses the supplied [seat function](../loquat/seats.py) and `AGREEMENTS_2026`, with the 3.25% threshold and 120 seats. **`shares` is the one-decimal display, balanced to exactly 100.0; `shares_unrounded` is the allocation input.** Keeping precision preserves the instruction to take the existing S1, S2, S3 and S10 series as computed. All scenarios use this same allocation convention. Reallocating from the display alone changes the following pairs, which are recorded explicitly rather than concealed:

| Scenario | Precise allocation | If seats were recomputed from the one-decimal display |
|---|---|---|
| S3 | Ra'am 6; Joint List 9 | Ra'am 5; Joint List 10 |
| S6 | Together 15; Yisrael Beiteinu 8 | Together 16; Yisrael Beiteinu 7 |
| S10 | Shas 8; Religious Zionism–Zehut 4 | Shas 7; Religious Zionism–Zehut 5 |
| S11 | UTJ 7; Yashar 21 | UTJ 8; Yashar 20 |

Judge mechanisms after the count using the signatures as well as seat errors. National shares use **all valid votes**, including failed lists. For turnout, use the frozen 2022 proxy classification where ballot-box matching is possible, report unmatched boxes, and report the official locality series separately. Do not reclassify communities by their new party choices and then call the resulting composition change a turnout change. Effective turnout requires the stated neutral envelope attribution; official results do not reveal voters' personal community membership. A matching signature supports a mechanism but does not uniquely establish why votes moved.

[check_scenarios.py](check_scenarios.py) checks all share and seat totals, the 15 ids, bloc membership, largest-list ties, the exact source files/rows/fields, citations for every size parameter, signatures and independent reconstruction of every mechanism. The checked result is saved in [validation.json](validation.json). Run the read-only check with:

```sh
/Users/jeanclaude/Documents/simczech/world/.venv/bin/python -B check_scenarios.py
```

[build_scenarios.py](build_scenarios.py) reproduces the set from saved inputs and writes a fresh `made_at`. Rebuilding after sealing changes the fingerprint; keep the checked files fixed for the external seal. Only files in this folder are written by these scripts.
