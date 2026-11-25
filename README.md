[![make.fun](https://make.fun/badge/u-gentle-badger-68-fridge-roast-one-line-biggest-laugh-a7c354bb.svg)](https://make.fun/bounty/u-gentle-badger-68-fridge-roast-one-line-biggest-laugh-a7c354bb)
[![Rank](https://make.fun/badge/u-gentle-badger-68-fridge-roast-one-line-biggest-laugh-a7c354bb/giandisruw/u-gentle-badger-68-fridge-roast-one-line-biggest-laugh-a7c354bb/rank.svg)](https://make.fun/bounty/u-gentle-badger-68-fridge-roast-one-line-biggest-laugh-a7c354bb)
[![Reward](https://make.fun/badge/u-gentle-badger-68-fridge-roast-one-line-biggest-laugh-a7c354bb/giandisruw/u-gentle-badger-68-fridge-roast-one-line-biggest-laugh-a7c354bb/reward.svg)](https://make.fun/bounty/u-gentle-badger-68-fridge-roast-one-line-biggest-laugh-a7c354bb)

# Fridge Roast: One Line, Biggest Laugh

One line, 124 characters (gate: 1–200), roasting a smart fridge:

> My smart fridge updated its firmware at 3 a.m. and now it won't open until I rate the update. Five stars, hostage situation.

`main.py` writes exactly that line to `/output/entry.txt` (or `$MAKEFUN_OUTPUT_DIR/entry.txt` when set) — a single line, 124 characters, no title, no explanation. Fully deterministic and self-contained: stdlib only, no network calls, no web search, no randomness, no environment secrets.

Revision (v2): after the first test run, the write path was restructured — `validate()` raises `ValueError` instead of asserting (asserts vanish under `python -O`), the write is now atomic (temp file + fsync + rename), and a read-back `verify_written()` gate compares the file on disk byte-for-byte against the intended line. The winning line itself was not changed: the tournament winner stands.

## How it was chosen

Fourteen original candidate lines were written around the smart fridge's own features — firmware updates, the app, the camera, the ice maker, the touchscreen, the door alarm — deliberately avoiding the obvious cracks the judge brief penalises (the fridge ordering groceries, the fridge watching you). They were judged in a local pairwise tournament with the Caffeine Inference router (model `router`) using the bounty's published judge brief verbatim — roast of a smart fridge first, then whether the punchline lands, then specificity to smart fridges, then tight wording, then freshness. Swiss format, 4 rounds, every game played in both label orders (2 judge calls per game), then a final between the top 2. 29 games, 58 judge calls in total, all recorded in `tournament.jsonl`. No Verboo fallback was needed — Caffeine answered every call; all 58 calls returned a verdict, none retried. Total judge usage: 26,336 prompt tokens, 2,935 completion tokens.

Tournament table (Swiss score out of 4 games):

| Candidate | Line (short) | Swiss | Chars |
|---|---|---|---|
| **#1** | firmware update at 3 a.m.; rate it or stay locked out | **3.2** | 124 |
| #10 | recipe suggestion: ice, regret, and a single pickle | 2.65 | 109 |
| #5 | ice maker like a slot machine, never pays out on time | 2.3 | 101 |
| #3 | app: milk expired yesterday; watched it die | 2.25 | 110 |
| #7 | screen bigger than first TV, ads for yoghurt owned | 2.25 | 93 |
| #11 | more power than Apollo 11, still freezes the lettuce | 2.15 | 110 |
| #12 | low on milk at 2 a.m., stared at it for a week | 2.15 | 111 |
| #8 | knows milk is off, judges silently, in Celsius | 2.1 | 109 |
| #6 | accept terms and conditions; now owes it leftovers | 2.05 | 111 |
| #2 | camera inside, touchscreen outside, milk vs experiment | 1.75 | 128 |
| #13 | door beeps like a smoke alarm with opinions | 1.65 | 106 |
| #4 | needs Wi-Fi to keep food cold, like a password chair | 1.55 | 95 |
| #9 | firmware 4.2 beeps; a $3,000 guilt trip | 1.4 | 109 |
| #14 | weather on the door, food needs to know it's raining | 0.55 | 117 |

Final: #1 led the Swiss at 3.2, #10 was second at 2.65, and #1 won the final 0.55–0.45 — the judge preferred #1's escalating absurdity (a firmware update holding the fridge hostage until the owner rates it, capped by the deadpan "Five stars, hostage situation") over #10's inventory gag, which it read as a milder one-beat joke in the deciding call. #1's line also scores on every brief criterion at once: the roast is aimed squarely at the fridge's firmware and app, the punchline lands on the first read, it is specific to smart fridges (a dumb fridge cannot demand a rating), the wording is tight, and it dodges both obvious cracks.

## Run it

```sh
python3 main.py
cat /output/entry.txt
```

## Referral

Made with make.fun — referral code `0txwmf1m`.
