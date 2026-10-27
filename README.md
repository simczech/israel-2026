# Simczech: Israel's Knesset election, 27 October 2026

Our prediction of the election to the 26th Knesset, sealed before the polls close and published when they close.
Page: [simczech.cz/world/israel/2026/parliament](https://simczech.cz/world/israel/2026/parliament)

## How it works

1. **Sealed.** Before the polls close we fix the prediction and publish only its fingerprint:
   `sealed/<election>/<version>/SHA256SUMS` lists the SHA-256 hash of every file of the prediction.
   The list carries independent timestamps: RFC 3161 tokens from FreeTSA and DigiCert, and an
   OpenTimestamps proof that is anchored in the Bitcoin blockchain within a few hours.
2. **Revealed.** When the polls close (22:00 Israel time, 21:00 CET), the files themselves are published in
   `predictions/<election>/<version>/`, next to a copy of the same list.
3. **Checked.** Anyone can confirm that the published files are the sealed ones, and that the list existed
   before the polls closed:

   ```sh
   # from the repository's top folder
   E=israel/2026/parliament; V=<version>
   cmp sealed/$E/$V/SHA256SUMS predictions/$E/$V/SHA256SUMS
   (cd predictions/$E/$V && shasum -a 256 -c SHA256SUMS)
   openssl ts -reply -in sealed/$E/$V/SHA256SUMS.freetsa.tsr -text
   ots verify sealed/$E/$V/SHA256SUMS.ots
   ```

Every prediction file contains a random number (`nonce`), so its fingerprint cannot be matched by trying out
possible results.

## Versions

| Version | Sealed | |
|---|---|---|
| `2026-10-26_2348` | 26 October 2026, 23:50 CET | The first version. |
| `2026-10-27_0146` | 27 October 2026, 01:48 CET, before the polls opened | The second version, shown on the page. |

Both seals were first published at those times in our general repository of election predictions and moved here on
27 October, before the polls opened, so that this election has a repository of its own. Git records the time of the move;
the timestamps of each list prove when it existed, independently of GitHub.

## Methods

Every method uses only material published before the polls opened: official results of past elections, registered
voters, published polls and other public sources.

- **Simczech Original** is the main prediction: 40 % Loquat, 35 % Lucuma, 15 % Carambola and 10 % Rambutan, a mix fixed
  before any of them produced a number.
- **Simczech Loquat** is a statistical model built on official past results and on published polls. It tests corrections
  for how Israeli polls erred in past elections and keeps only those that would have improved its own past predictions.
- **Simczech Lucuma** is analysts' research of sources published before the polls opened: polls and how they erred in
  the past, betting markets, the campaign. Six independent runs in the first version, ten in the second.
- **Simczech Carambola** moves Loquat's figures by social-media engagement: the reactions drawn by the Facebook posts of
  each list's leaders in the two weeks before the vote, against the list's share in the polls. In the first version its
  size was set by the same comparison before the 2021 and 2022 elections. For the second version the comparison was
  extended to September 2019 and 2020; the signal did not hold there, so in that version Carambola moves nothing.
- **Simczech Rambutan** is archetype opinions: groups of voters by their 2022 vote and where they live, sized by the
  official counts, each answering as a simulated voter from a campaign brief that leaves out the polls and the betting
  markets.

## Files of a prediction

- `prediction.json`: the national figures of every method (vote shares with 80 % ranges, seats with ranges, the blocs,
  turnout, probabilities).
- `sectors.csv`: the main prediction by community: Jewish not Haredi, Haredi, Arab, Druze.
- `runs/`: each method's own estimate as it was delivered.
