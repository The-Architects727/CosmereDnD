# Mistborn: A Metallic Arts Expansion for Fifth Edition

A homebrew expansion bringing Allomancy, Feruchemy, and Hemalurgy from Brandon
Sanderson's **Mistborn** novels to **D&D 5e (2024 ruleset)**.

It is built to be **true to Scadrial but played anywhere.** The rules assume an
ordinary D&D world with ordinary D&D magic in it, not a Scadrial campaign, so a
Coinshot can sit at the table next to a wizard and neither one breaks. How the
Metallic Arts and the Weave interact is settled explicitly rather than left to
the DM (see *The Arts and the Weave*, in the appendix).

**[The book](final-render/mistborn-homebrew.md)** is written for
[Homebrewery](https://homebrewery.naturalcrit.com/). Paste the file in and it
renders complete: the stylesheet is embedded at the top of it, and the finished
art is linked from this repository, so there is nothing else to set up.

---

## What is in it

### Part 1: Bloodlines

The Metallic Arts themselves, and the largest part of the book.

- **All sixteen Allomantic metals**, one entry per Misting, with the burn rules
  for each. Metal is spent in **charges**; a charge buys an instant, a round, or
  a minute of effect depending on the metal. Flaring costs extra charges and is
  capped by character level.
- **All sixteen Feruchemical metals**, one entry per Ferring. Storing and
  tapping are split into **Rate** (how hard you can draw) and **Depth** (how far
  past normal you can push), so a Feruchemist scales without becoming a god at
  level 5. Storing multiple attributes at once compounds against you.
- **Steel and Iron force tables**, so Pushing and Pulling is a lookup, not
  physics homework at the table.
- **Savants.** Burning a single metal long enough fuses you to it. Savancy is
  the *only* way past the flare cap, and it always carries the Dependency, even
  for a Mistborn. The threshold is measured in grams burned over a lifetime.
- **Twinborn and Compounding**, including what each of the sixteen pairings
  actually turns you into.
- **The god metals**: atium, malatium, lerasium.

### Part 2: Species

- **Kandra.** An Ooze that digests a corpse and wears it. The skeleton it wears
  sets its AC, it can go boneless, and it does not die so much as fall apart.
- **Koloss-blooded.** Grows for its whole life, from Medium to Huge, gaining
  Strength and size as its skin fails to keep up with its bones.

### Part 3: Backgrounds

Five backgrounds portable to any setting (Alloyer, Hazekiller, Crewmember,
Metal Smuggler, Ashworker) with two origin feats.

### Part 4: Classes

Three full classes to 20th level.

- **Mistborn.** Burns all sixteen metals against a level-scaled burn budget.
- **Feruchemist.** Runs many metalminds at once, masters quadrants, and ends up
  able to hold two metals inside their own body.
- **Hemalurgist.** Steals powers by driving spikes, rolling yield against the
  donor and placement against the body, and carries the risk of being controlled
  through the spikes they bear.

### Part 5: The Metal Economy

What metals cost, what a vial actually buys you in charges and in seconds, how
available each metal is, and what impure metal does to you.

### Appendix: The Arts and the Weave

The crossover layer. Magic cannot touch the Arts; six metals reach back into
magic. Defines exactly what a spell can and cannot do to a burning Allomancer.

---

## Repository layout

```
final-render/
  mistborn-homebrew.md   <- paste this into Homebrewery
  art/                   <- charts and illustrations, served from here
  README.md              <- art specification: slots, aspect ratios, how to add
```

The design vault this is generated from is kept private. This repository holds
only the finished, player-facing book and its art.

## Art

The three metal charts (Allomancy, Feruchemy, Hemalurgy) are complete and
included as SVG. The remaining illustration slots render as sized placeholders
that name what belongs there. Adding one is a matter of dropping a correctly
named file into `final-render/art/`; see
[the art README](final-render/README.md) for the slot list and the required
aspect ratios.

## Credit

Mistborn, Allomancy, Feruchemy, Hemalurgy, and the world of Scadrial are the
creations of **Brandon Sanderson**. This is unofficial fan work, made for play
at a home table and offered freely. It is not affiliated with Dragonsteel
Entertainment or with Wizards of the Coast.
