# Trio Corporate Live

Live scores, groups and playoff brackets for the Trio Corporate Tournament, Trio Padel Arena (Dummar Project, Damascus), 8–10 Oct 2026.
Link: https://triopadel.github.io/triocorporate/ (organization `triopadel` for Trio Padel Arena, one repo per tournament) · Firebase project `padeltournament-ed489` (same as Kinza, same scorekeeper logins).
Data: `tournaments/triocorporate/matches`, `/groups`, `/config` (the rules doc).

## Files
| File | What it is |
|---|---|
| `index.html` | The public page. Anyone watches; scorekeepers sign in to score. |
| `manifest.json`, `sw.js`, `icons/` | Installable app. Bump `VERSION` in `sw.js` after every upload. |
| `firestore.rules` | Rules for every tournament (Kinza root collections + `tournaments/<slug>/...`). |

## Setup
1. GitHub: create the organization `triopadel`, then a repo `triocorporate` inside it. Upload everything in this folder, then Settings → Pages → deploy from `main` / root.
2. Firebase → Authentication → Settings → Authorized domains → add `triopadel.github.io`.
3. Firestore → Rules: paste `firestore.rules` → Publish. (Kinza keeps working.)
Keepers and logins are shared with Kinza, so nothing else to do in Firebase.

## Running the tournament (signed in as scorekeeper)
- **Groups tab → Add a group**: category, letter, one team per line, `Player + Player (Company)`.
- **Create matches** next to each group makes every group match on Day 1 with no time; tap each one to set time and court.
- **Playoffs tab → Set up these playoff matches** once per category. Teams fill in automatically when a group is finished
  (every group match Final), and winners move forward as matches are marked Final. Typing a team in a playoff match overrides the slot.
- **Info tab → Set undecided rules**: 40–40 rule, third set in semis/final (full set or tie-break to 10), third-place match.
  Until set: one advantage then golden point; full third set; no third-place match.

## Formats built in
- A: groups 1 set to 6 · QF best of 3 with tie-break to 10 at one set all · SF/F best of 3.
- B: groups 1 set to 6 · R16 and QF 1 set to 9 (tie-break at 8–8) · SF/F best of 3.
- Bracket: B R16 1A–4D, 2B–3C, 4B–1C, 2D–3A | 1B–4C, 2A–3D, 1D–4A, 2C–3B. A QF 1A–4B, 2B–3A | 2A–3B, 1B–4A.
