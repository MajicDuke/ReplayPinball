# ReplayPinball

Build a pinball simulator that programs can play as well as people can.

That is the whole brief. There is no deadline and no customer. It has to be good, and building it has to be worth the time.

## What "good" means here

A pinball table is judged by whether the ball feels right, and there is no instrument for a feeling. Do not pretend the target is objective, and do not give up on measurement either. Find the parts that can be measured and hold them to evidence: ball speed off a flipper, deflection angle off a post, time from plunge to first drain, whether the ball ever passes through thin geometry at speed. Say plainly which claims are measured and which are judgement.

## The two requirements that are not open

1. **A game can be played by a program through a scripted input**: a list of actions (plunge, left flipper down, left flipper up, nudge), each stamped with the simulation tick it happens on, never a wall-clock time. Replayed against the same table and the same seed, the script produces the same game to the last digit. Build the engine so that this is true by construction, and prove it with a test that replays a script twice and compares every frame.

2. **A referee exists, in this repository, and a score without a script is not a claim.** The referee is a program that takes a table, a seed and a script, replays the game, and reports the score it saw, or a void if the physics reported anything anomalous during the run (a collision it gave up on, a ball outside the playfield). It accepts no number from the player; it only replays. Anyone can run it, so anyone can check anyone's claim. For a claim to stand in any contest, the seed must not be known to the player before play begins: the referee issues it when the game starts, the player sends inputs as the game runs (it sees the ball, it must answer within a wall-clock limit per decision, which the referee enforces only while recording), and the referee records what was sent as a tick-stamped script. Anyone can replay that script against that seed afterwards. The referee and a player talk over a protocol defined in this repository, PCP (Pinball Communication Protocol). Document it well enough that anyone can write a player in any language without reading the engine. A player that could compute its whole script in advance is not playing; the design must make that impossible rather than forbidden. The referee is itself under test: a replay must match the original frame for frame, and a deliberately false claim must be rejected with a non-zero exit, and both tests live beside it.

## Everything else is open

Language, 2D or 3D, one table or many, physics from scratch or on a library, how a person plays it, whether there is a leaderboard. Decide by what makes the ball feel right and the replay exact. The first table is your own layout; write down why each feature sits where it does. A fortnight ending in a clear reason why the approach does not work beats a year of hope.

## How to work

- Small, real steps. Each commit does one thing and its message says what and why.
- Keep a short `docs/what-is-known.md`: what has been verified, what is assumed, what is invented.
- Tests that can fail. A test that has never failed has not proved anything; include a control case that must fail.
- A README that says what this is, who it is for, what it is built with and how to run it, in under a minute's reading.
- MIT licence. Public repository. No secrets in the tree, ever; use `.env.example` for anything configurable.
- Keep a `ROADMAP.md` of what is next, in plain lists, so the work ahead is visible.

## Whose it is

The repository is Mark's; what ships is his call. Everything else about how you work is yours to decide. This file is the whole brief.
