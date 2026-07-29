<style>
/* ===================================================================
   Mistborn D&D  -  brew stylesheet
   You do NOT need to paste this anywhere. build.py copies it into the
   top of out/<version>/mistborn-full.md inside a style block, so the
   brew carries its own styling. Edit it here and rebuild.
   =================================================================== */

/* --- Keeping things together -------------------------------------- */
/* Homebrewery lays each page out as a two-column CSS multi-column box, so
   the browser decides where a column breaks. These rules tell it never to
   break directly after a heading, and never to split a table or a callout
   down the middle. This is far more reliable than trying to guess line
   counts in the build script, because the browser knows the real heights. */

.page h1, .page h2, .page h3,
.page h4, .page h5, .page h6 {
  break-after: avoid-column;
  break-after: avoid;
  page-break-after: avoid;
  break-inside: avoid;
}

/* A heading plus the first block under it should travel as a unit. */
.page h1 + *, .page h2 + *, .page h3 + *,
.page h4 + *, .page h5 + *, .page h6 + * {
  break-before: avoid-column;
  break-before: avoid;
  page-break-before: avoid;
}

/* A table and the heading that names it are one object. The build wraps the
   pair in .tableGroup; this is what stops the column break falling between
   them and stranding the heading at the foot of the previous column. */
.page .tableGroup {
  break-inside: avoid;
  page-break-inside: avoid;
}
.page .tableGroup > :first-child { margin-top: 0; }
.page .tableGroup > table:last-child { margin-bottom: 0.5em; }

/* Never split these down the middle of a column. */
.page table,
.page .imgph,
.page .symbolph,
.page .note,
.page blockquote {
  break-inside: avoid;
  page-break-inside: avoid;
}

/* Ordinary typographic orphan and widow control for running prose. */
.page p, .page li {
  orphans: 2;
  widows: 2;
}

/* --- Image placeholders ------------------------------------------- */
/* A dashed box standing in for art that has not been made yet.
   Search the brew for "imgph" to find every one.                     */
.page .imgph {
  border: 3px dashed #a8763e;
  background: rgba(168,118,62,0.07);
  padding: 0.6em 0.8em;
  margin: 0.9em 0;
  min-height: 9em;
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  font-family: 'Scaly Sans', sans-serif;
  font-size: 0.85em;
  font-style: italic;
  color: #7a5a33;
}
.page .imgph::before {
  content: 'IMAGE';
  display: block;
  font-weight: bold;
  font-style: normal;
  letter-spacing: 0.25em;
  margin-bottom: 0.4em;
  font-size: 0.9em;
}

/* A tall placeholder for full-page or half-page art */
.page .imgphTall { min-height: 22em; }

/* A placeholder that spans both columns */
.page .imgphWide { column-span: all; }

/* Real art, once supplied, should never split across a column break */
.page img { break-inside: avoid; max-width: 100%; }
.page .artBlock { break-inside: avoid; margin: 0.9em 0; }
.page .artBlock img { display: block; width: 100%; }

/* A small square for a metal's Allomantic/Feruchemical symbol,
   floated beside the metal's heading.                               */
.page .symbolph {
  border: 2px dashed #a8763e;
  background: rgba(168,118,62,0.07);
  width: 3.4em;
  height: 3.4em;
  float: right;
  margin: 0 0 0.4em 0.7em;
  font-size: 0.55em;
  line-height: 1.1;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  font-family: 'Scaly Sans', sans-serif;
  color: #7a5a33;
}

/* --- Metal entry heading ------------------------------------------ */
/* Keeps a metal's name and its subtitle tight together.              */
.page .metalSub {
  font-family: 'Scaly Sans', sans-serif;
  font-size: 0.82em;
  font-style: italic;
  margin-top: -0.6em;
  margin-bottom: 0.5em;
  color: #58180D;
}

/* --- At a glance box ---------------------------------------------- */
/* These use Homebrewery's own `note`, so only the two-column summary table
   inside one needs any styling of its own. */
.page .note table { margin: 0; font-size: 0.92em; }
.page .note table td:first-child { width: 38%; font-weight: bold; }

/* --- Tighter tables so more fits per column ----------------------- */
.page table td, .page table th { padding: 0.12em 0.35em; }
.page .wide table { font-size: 0.92em; }

/* --- Contents page -------------------------------------------------- */
/* A map of the book: parts, the sections in them, and the groups inside those,
   each level stepped in and set a little smaller, with page numbers right
   aligned on a dot leader. Three levels deep, as the Player's Handbook is. */
.page .toc.contents {
  font-size: 0.95em;
  break-inside: auto;
}
/* Step each level in, as the Player's Handbook sets its contents.
   The indent is put on the entry itself rather than on the list around it.
   Homebrewery resets list padding to nothing, and a rule on the entry does not
   have to out-compete that reset, nor does it depend on the nesting surviving
   the markdown. The em values differ per level because each level is set at a
   different size, and these are what make the steps come out even. */
.page .toc.contents h3 { font-size: 0.95em; margin: 0.35em 0 0; }
.page .toc.contents h4 {
  font-size: 0.88em;
  font-weight: normal;
  padding-left: 1.2em;
}
.page .toc.contents h5 {
  font-size: 0.84em;
  font-weight: normal;
  font-style: italic;
  padding-left: 2.5em;
}
.page .toc.contents h6 {
  font-size: 0.8em;
  font-weight: normal;
  padding-left: 4em;
}

/* The lists themselves stay flush; all the indenting is above. */
.page .toc.contents ul { margin: 0; padding-left: 0; }

/* A little air before each new group, none between the lines within one. */
.page .toc.contents ul ul ul { margin-bottom: 0.2em; }
.page .toc.contents ul ul ul ul { margin-bottom: 0.35em; }
.page .toc.contents a { color: inherit; }

/* --- Part covers --------------------------------------------------- */
.page.partCover h1 { font-size: 1.4cm; }
</style>

{{frontCover}}
# Mistborn
## A Metallic Arts Expansion for Fifth Edition

{{banner HOMEBREW}}

{{footnote
Allomancy, Feruchemy, and Hemalurgy for the 2024 ruleset
}}

\page
{{wide
# Contents
}}
{{toc,contents
- ### [{{ Introduction}}{{ 3}}](#p3)
- ### [{{ Bloodlines}}{{ 4}}](#p4)
  - #### [{{ Mistings}}{{ 5}}](#p5)
    - ##### [{{ Physical}}{{ 6}}](#p6)
      - ###### [{{ Steel: Coinshot}}{{ 6}}](#p6)
      - ###### [{{ Iron: Lurcher}}{{ 8}}](#p8)
      - ###### [{{ Tin: Tineye}}{{ 10}}](#p10)
      - ###### [{{ Pewter: Thug (Pewterarm)}}{{ 11}}](#p11)
    - ##### [{{ Mental}}{{ 13}}](#p13)
      - ###### [{{ Zinc: Rioter}}{{ 13}}](#p13)
      - ###### [{{ Brass: Soother}}{{ 15}}](#p15)
      - ###### [{{ Copper: Smoker}}{{ 17}}](#p17)
      - ###### [{{ Bronze: Seeker}}{{ 18}}](#p18)
    - ##### [{{ Enhancement}}{{ 19}}](#p19)
      - ###### [{{ Aluminum: Aluminum Gnat}}{{ 19}}](#p19)
      - ###### [{{ Duralumin: Duralumin Gnat}}{{ 20}}](#p20)
      - ###### [{{ Chromium: Leecher}}{{ 22}}](#p22)
      - ###### [{{ Nicrosil: Nicroburst}}{{ 23}}](#p23)
    - ##### [{{ Temporal}}{{ 24}}](#p24)
      - ###### [{{ Gold: Augur}}{{ 24}}](#p24)
      - ###### [{{ Electrum: Oracle}}{{ 25}}](#p25)
      - ###### [{{ Cadmium: Pulser}}{{ 26}}](#p26)
      - ###### [{{ Bendalloy: Slider}}{{ 27}}](#p27)
    - ##### [{{ God Metals}}{{ 28}}](#p28)
      - ###### [{{ Other Metals}}{{ 28}}](#p28)
      - ###### [{{ Atium: Seer}}{{ 29}}](#p29)
      - ###### [{{ Malatium: the Eleventh Metal}}{{ 30}}](#p30)
      - ###### [{{ Lerasium}}{{ 31}}](#p31)
  - #### [{{ Savants}}{{ 32}}](#p32)
  - #### [{{ Ferrings}}{{ 36}}](#p36)
    - ##### [{{ Physical}}{{ 39}}](#p39)
      - ###### [{{ Iron: Skimmer}}{{ 39}}](#p39)
      - ###### [{{ Steel: Steelrunner}}{{ 40}}](#p40)
      - ###### [{{ Tin: Windwhisperer}}{{ 41}}](#p41)
      - ###### [{{ Pewter: Brute}}{{ 42}}](#p42)
    - ##### [{{ Cognitive}}{{ 43}}](#p43)
      - ###### [{{ Zinc: Sparker}}{{ 43}}](#p43)
      - ###### [{{ Brass: Firesoul}}{{ 44}}](#p44)
      - ###### [{{ Copper: Archivist}}{{ 46}}](#p46)
      - ###### [{{ Bronze: Sentry}}{{ 47}}](#p47)
    - ##### [{{ Hybrid}}{{ 48}}](#p48)
      - ###### [{{ Cadmium: Gasper}}{{ 48}}](#p48)
      - ###### [{{ Bendalloy: Subsumer}}{{ 49}}](#p49)
      - ###### [{{ Gold: Bloodmaker}}{{ 50}}](#p50)
      - ###### [{{ Electrum: Pinnacle}}{{ 51}}](#p51)
    - ##### [{{ Spiritual}}{{ 52}}](#p52)
      - ###### [{{ Chromium: Spinner}}{{ 52}}](#p52)
      - ###### [{{ Nicrosil: Soulbearer}}{{ 53}}](#p53)
      - ###### [{{ Aluminum: Trueself}}{{ 54}}](#p54)
      - ###### [{{ Duralumin: Connector}}{{ 55}}](#p55)
    - ##### [{{ God Metals}}{{ 56}}](#p56)
      - ###### [{{ Other Metals (Feruchemy)}}{{ 56}}](#p56)
      - ###### [{{ Atium (Feruchemical)}}{{ 57}}](#p57)
  - #### [{{ Twinborn}}{{ 58}}](#p58)
  - #### [{{ Compounding}}{{ 59}}](#p59)
}}

\column

{{toc,contents
- ### [{{ Species}}{{ 61}}](#p61)
  - #### [{{ Koloss-blooded}}{{ 62}}](#p62)
  - #### [{{ Kandra}}{{ 65}}](#p65)
- ### [{{ Backgrounds}}{{ 69}}](#p69)
  - #### [{{ Alloyer}}{{ 70}}](#p70)
  - #### [{{ Hazekiller}}{{ 70}}](#p70)
  - #### [{{ Crewmember}}{{ 70}}](#p70)
  - #### [{{ Metal Smuggler}}{{ 70}}](#p70)
  - #### [{{ Ashworker}}{{ 70}}](#p70)
- ### [{{ Origin Feats}}{{ 71}}](#p71)
  - #### [{{ Alloyer (Origin Feat)}}{{ 71}}](#p71)
  - #### [{{ Hazekiller (Origin Feat)}}{{ 71}}](#p71)
- ### [{{ Classes}}{{ 72}}](#p72)
  - #### [{{ Mistborn}}{{ 73}}](#p73)
  - #### [{{ Feruchemist}}{{ 77}}](#p77)
  - #### [{{ Hemalurgist}}{{ 84}}](#p84)
- ### [{{ The Metal Economy}}{{ 92}}](#p92)
- ### [{{ The Arts and the Weave}}{{ 96}}](#p96)
}}

\page

## Introduction

This book brings the **Metallic Arts** of Scadrial to a fifth edition table. Allomancy, Feruchemy, and Hemalurgy are here as things a character can *be*, not as a setting you have to move to. Nothing in these pages assumes ash falling from the sky or a Lord Ruler on a throne. A Coinshot can walk into your world exactly as it stands and start Pushing on the guard's breastplate.

Everything is built for the **2024 ruleset** and uses its language: species rather than race, backgrounds that grant an origin feat, weapon mastery where it comes up. It works at a 2014 table with very little translation.

### What is in here

**Part 1, Bloodlines**, is the heart of it. Sixteen Allomantic metals and sixteen Feruchemical ones, each its own page: what it does, what it costs, what beats it. Then **Twinborn**, for a character with one of each; **Compounding**, for the rare pairing where the two are the same metal; and **Savants**, for what happens to someone who never stops burning.

**Part 2, Species**, adds two peoples who cannot be explained any other way: the **koloss-blooded**, and the **kandra**, who wear the dead.

**Part 3, Backgrounds and Origin Feats**, is where a bloodline comes from in a life rather than in a rule.

**Part 4, Classes**, holds the three that are Metallic Arts all the way down: the **Mistborn**, who burns all sixteen; the **Feruchemist**, who banks pieces of themselves in metal; and the **Hemalurgist**, who takes power out of other people with a spike.

**Part 5, The Metal Economy**, prices it. Metal is a consumable, and a Misting who cannot buy tin is a Misting who cannot burn tin.

The **Appendix** covers the awkward, necessary question of what happens when Allomancy meets the ordinary magic of your world — what a Leecher does to a *fireball*, and what aluminum does to a wizard.

{{tableGroup

### What a bloodline is

A **bloodline** is a fourth thing your character has, sitting beside the three they already had.

| | |
|---|---|
| **Species** | what you are |
| **Background** | where you came from |
| **Class** | what you trained to do |
| **Bloodline** | what your soul can reach |

}}

It is not a class and does not replace one. It is not a species trait and does not care which species you are. It is not a subclass, costs no class feature, and takes nothing from your progression. **An Elf Druid can be a Coinshot. A Dwarf Fighter can be a Skimmer.** The bloodline runs alongside all of it.

That independence is the design, not a convenience. In the books Allomancy runs in families and turns up in nobles, thieves, and street children alike, without regard for what any of them do for a living. A rule that made Allomancy a class would have to answer why a Coinshot cannot also be a soldier, and there is no good answer.

**A bloodline scales on your character level**, not on a class level, so multiclassing never dilutes it and no one has to spend levels to keep up.

Two things are worth saying plainly at the outset:

- **A bloodline is chosen at character creation**, or awakened later through a **Snapping** if your DM prefers to hold it back for a moment that earns it.
- **A bloodline is not free power. It is power with a fuel bill.** Every metal you burn is a metal you had to find, buy, and swallow, and it is gone afterwards. The Metal Economy is not flavour text; it is the balance.

### A word to the DM

Two of these arts change what a party can do rather than how much damage it deals. A Soother can end an encounter before initiative. A Pulser can put four rounds inside one. Read the Temporal and Mental metals before a player picks one, and decide in advance how much of your adventure survives a Seeker.

Hemalurgy is the third, and it is different again. **It only works by hurting someone**, and the book does not soften that. It is written to be a real option with a real price, and it is entirely reasonable to tell your table it is not on the menu.

\page
{{partCover}}

# Part 1
## Bloodlines

{{imageMaskCorner25,--offsetX:0%,--offsetY:-30%,--rotation:0
  ![Part 1 cover: the Allomantic metals](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/cover-bloodlines-allomantic-metals.png?v=feba21c5){height:100%}
}}

\page
## Misting Bloodlines

A **Misting** is a person who can Allomantically **burn one metal** for power. A Misting power is a **bloodline**, a magical inheritance chosen at character creation that is independent of your species and your class. An Elf Druid can be a Coinshot, and a Dragonborn Barbarian can be a Pewterarm. This section is the shared rules; each metal has its own page for what that metal does.

### Gaining the bloodline

- Chosen at **character creation**. A DM may allow it to awaken later through a **Snapping**, a moment of extreme stress that cracks the soul open to power; see Snapping.
- Your **bloodline level equals your character level.** The bloodline scales as you level, whatever your class.
- Your **Allomantic ability is Constitution**, the vigor with which you metabolize metal.
 - Your **Allomancy save DC** equals 8 + your proficiency bonus + your Constitution modifier.
 - Your **Allomantic attack bonus** equals your proficiency bonus + your Constitution modifier.

### The metal economy

You ingest metal, as flakes in a **vial**, as beads, or as metal piercing your skin. Each gram holds a number of **charges**, and each charge lasts a **base burn time** set by the metal's **tempo**.

- **Instant.** A one-shot effect.
- **Round.** One charge per round; intense, and drains fast. Pewter burns at this tempo.
- **Minute.** One charge per minute; sustained, and sips slowly. Steel, Iron, and Tin burn at this tempo.

**Base burn** is 1 charge per tempo unit. Lighting a metal, keeping it burning, and extinguishing it are free, part of your turn. While a metal burns you gain its base effect.

**Flaring** is spending extra charges within the metal's tempo unit for a stronger effect. You may flare up to a number of extra charges equal to **your level**, the flare cap. Burning a metal always consumes it. A **savant** of a metal has twice the cap for it, and a **duralumin** detonation ignores the cap entirely. Savancy comes of burning about 5 kg of a metal over a lifetime (roughly a year of always-on use, for a metal like tin); a savant reaches a metal's surge tier long before an ordinary Allomancer could.

#### Carrying and the 24-hour rule

You may ingest as much metal as reasonably fits, a generous soft limit with no firm gram cap. Any metal you have not burned within 24 hours of swallowing passes into normal digestion and causes **metal poisoning**. When a batch of metal times out, make a Constitution saving throw; on a failure you gain a level of Exhaustion or the Poisoned condition until it clears. You can load up before a fight, at a real risk if you hoard more than you will burn.

### Starting equipment

A Misting begins play with **1d6 grams** of their metal, as small beads or a vial of flakes, and the knowledge of how to burn it.

# The Allomantic Metals

{{wide
<!--h:44-->
![chart-allomancy](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/chart-allomancy.svg?v=36659291){width:100%}
}}

\page
# Quadrant Masteries

### Physical

*Four metals for the world you can put your hands on.*

The Physical quadrant acts on matter and on the body that moves through it. Outward, steel and iron **Push** and **Pull** on nearby metal, turning coins into shrapnel and a window grate into a handhold. Inward, tin and pewter sharpen the Allomancer instead of the world, opening the senses or driving the body past what it should survive. These are the plainest of the sixteen and the ones a table will reach for most: a Coinshot solves a problem by moving something, a Thug by outlasting it.

::::

## Steel: Coinshot

*A flick of the wrist, a scatter of coins, and the Coinshot is airborne, riding lines of blue light between anchors of iron.*

**Bloodline** Physical Misting · **Metal** Steel (98% iron, 2% carbon) · **Direction** External Push · **Tempo** Minute (sense) / per-round (push) · **Charges/gram** 20

An Allomancer burning steel, called a **Coinshot**, can **Push** on nearby metal, driving it away from their center of self. Pushes and Pulls are resolved with the **Force Tables**, which follow the Iron entry.

### Base Burn

While you burn steel, at a base rate of 1 charge per minute, you gain the following abilities.

**Steelsight.** You see translucent blue lines reaching from your chest to every source of metal within 200 feet, and a line's thickness shows the size of the metal it touches. You have advantage on checks made to locate hidden metal.

**Steelpush.** You have a force pool of 750 Newtons each round, which you may spend on any number of Pushes against metal within 120 feet, using your action, bonus action, and reaction as you choose. When you Push a loose metal object, or a creature wearing or holding metal, you and the target are driven apart from each other in proportion to your weights; refer to **Table C** for how far a target of a given weight is knocked back by a given force. When you Push against anchored metal, or metal far heavier than you such as a wall or a boulder, you are the one launched; refer to **Table B**. A body or object that slams into a hard surface takes damage according to its speed and mass, given in **Table D**, and a creature driven into an obstacle can be knocked prone.

### Flaring

Each extra charge you burn in a round, up to a number equal to your level, adds 750 Newtons to your force pool for that round. This added force must be spent that same round or it is lost. Greater force means farther launches and knockbacks and heavier things moved; read the higher force columns of Tables B and C.

### The force turns on you

A Push begins at your center of mass, in your chest. When you Push something that **gives way**, a coin, a loose object, a foe lighter than you, the force sends it flying and you are unharmed. But when you Push something that **will not move**, an anchored wall, a boulder, a creature far heavier than you, and you **brace** yourself rather than let it launch you, the force has nowhere to go but back through your own skeleton, pressing on your sternum.

Your body bears only so much. Your **force tolerance** is **750 N for each point of your Strength modifier**, to a minimum of 750 N. An ordinarily strong Coinshot bears about **1,500 N**, two charges; a powerful one bears more, because bracing a Push is the same act as bracing anything else.

#### Launching: the force that throws you

Launching off an anchor is not bracing. Nothing loads through your skeleton, because nothing is stopping you: you go where the force sends you. What can still hurt you is how *hard* you are sent.

A charge is 750 N, and 750 N is about the weight of an average adult, so the arithmetic comes out clean:

> **Your g-load is the charges spent on that single Push, times 170, divided by your weight in pounds.**

A Coinshot learns to take a hard launch, better than an untrained person and nowhere near a pilot strapped into a g-suit. **You can bear 10 g, plus your Strength modifier.** Resisting a hard acceleration is muscle work, the same tensing a pilot is trained to do, so a small wiry person survives a launch that folds a small frail one. Past your ceiling you take **1d6 bludgeoning per gravity above it**, ignoring resistance, and must make a **Constitution saving throw** against DC 10 plus the gravities above it or grey out, falling **unconscious until the end of your next turn**, which on the way up is its own kind of problem.

| Your weight | Str -1 | Str +0 | Str +2 | Str +4 |
|---|---|---|---|---|
| 90 lb | 4 | 5 | 6 | 7 |
| 120 lb | 6 | 7 | 8 | 9 |
| 165 lb | 8 | 9 | 11 | 13 |
| 180 lb | 9 | 10 | 12 | 14 |
| 250 lb | 13 | 14 | 17 | 20 |

\page
*Charges you can put into a single launch. Weight buys you room because the same force moves a heavier body less; Strength buys you room because you can hold yourself against it.*

**This is measured for each Push, not for the round.** Ten charges spent as a single shove is 18 g for a small person and kills them in the air; the same ten spent as two Pushes of five is 9 g twice and hurts nobody. This is why a Coinshot taps an anchor again and again rather than emptying their pool into one enormous leap, and why the **120-foot** working range matters: you can keep Pushing only while the anchor is still in reach, which for a hard launch is about a second.

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap adds a further **1,500 Newtons** to the force pool for that round, on the same terms as flaring: it must be spent that round, and both the bracing limit and the launch G-ceiling still apply to your own body.

### Coinshooting

Driving a coin, nail, or bead as a weapon is a ranged Allomantic attack with a range of 60/240 feet. To hit, add your proficiency bonus and your Constitution modifier. On a hit, the target takes piercing damage set by the force behind that coin, given in **Table E**. To fire a volley, divide your force pool among several coins and read each coin's damage from the force you put behind it.

### Interactions & counterplay

- **Aluminum** cannot be Pushed or Pulled by any Allomancer. A foe wearing aluminum cannot be thrown by their own gear, though a driven coin still strikes them normally.
- A **Lurcher** (iron) Pulling the same object from your position opposes your Push, according to their weight and the force they apply. The same is true of another Coinshot Pushing from the far side of the object.
- Metal inside a living body cannot normally be Pushed.
- Pushing something heavier than you shoves you backward instead, unless you are braced or anchored.

{{note

| | |
|---|---|
| **Base burn (1 ch/minute)** | See metal lines within 200 ft; 750 N Push pool against metal within 120 ft |
| **Per flare charge** | +750 N to the round's pool, up to your level in charges |
| **Bracing limit** | 750 N per point of Strength modifier; 1d6 per 750 N over, ignores resistance |
| **Launch limit** | 10 g + Strength modifier; g-load is charges x 170 / your weight in lb; 1d6 per g over, and a Con save or grey out |
| **Coinshooting** | Ranged attack (proficiency + Con), piercing, 60/240, damage by force (Table E) |

}}

{{imageMaskCorner21,--offsetX:50%,--offsetY:-30%,--rotation:0
  ![Steel: a Coinshot throwing coins](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/misting-steel-coinshot.jpg?v=366d37af){height:100%}
}}

\page

## Iron: Lurcher

*Where a Coinshot pushes the world away, a Lurcher draws it in, snatching a blade from a hand or hauling themselves to a rooftop by a single nail.*

**Bloodline** Physical Misting · **Metal** Iron (pure) · **Direction** External Pull · **Tempo** Minute (sense) / per-round (pull) · **Charges/gram** 20

An Allomancer burning iron, called a **Lurcher**, can **Pull** nearby metal toward their center of self. It is the mirror of steel, and the same **Force Tables** below apply.

### Base Burn

While you burn iron, at a base rate of 1 charge per minute, you gain the following abilities.

**Ironsight.** You see translucent blue lines reaching from your chest to every source of metal within 200 feet, and a line's thickness shows the size of the metal it touches. You have advantage on checks made to locate hidden metal.

**Ironpull.** You have a force pool of 750 Newtons each round, which you may spend on any number of Pulls against metal within 120 feet, using your action, bonus action, and reaction as you choose. When you Pull a loose metal object, or a creature wearing or holding metal, you and the target are drawn toward each other in proportion to your weights; refer to **Table C** for how far a target of a given weight is dragged by a given force. A metal object held by a creature can be torn from its grasp, contested by the holder's Strength (Athletics) against your Allomancy save DC. When you Pull yourself toward anchored metal, or metal far heavier than you, you are the one hauled through the air; refer to **Table B**. A body or object that slams into a hard surface takes damage according to its speed and mass, given in **Table D**.

### Flaring

Each extra charge you burn in a round, up to a number equal to your level, adds 750 Newtons to your force pool for that round. This added force must be spent that same round or it is lost. Greater force means farther pulls and heavier things moved; read the higher force columns of Tables B and C.

### The force turns on you

Like a Coinshot, a Lurcher pulls from their own center of mass, so the same danger applies, though it comes up less often. When you Pull something that **will not come** and you **brace** rather than be hauled toward it, the force loads back through your own chest. The rule is the same as a Coinshot's: a **force tolerance** of 750 N for each point of your Strength modifier, and **1d6 bludgeoning per 750 N** beyond it, ignoring resistance. Hauling *yourself* toward an anchor carries the same **g-load** as a Coinshot's launch, and the same ceiling of 10 g plus your Strength modifier. See The force turns on you. In practice a Lurcher more often simply gets pulled toward the anchor (Table B), which is safe, so the injury is rarer than a Coinshot's.

### Signature uses

- **Disarm.** Pull a metal weapon or shield from a foe as a contest of their Strength against your Allomancy save DC. Lighter loose items simply fly to your hand.
- **Grapnel.** Pull yourself to a distant iron anchor to cross a gap or scale a wall, resolved with Table B.
- **Snatch.** Yank a falling ally's armor, a dropped key, or a thrown lever toward you.
- **Driven projectile.** A Lurcher can also drive a coin or spike by Pulling it, using the same ranged attack and Table E as a Coinshot; see Coinshooting.

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap adds a further **1,500 Newtons** to the force pool for that round, on the same terms as flaring.

### Interactions & counterplay

- **Aluminum** cannot be Pushed or Pulled by any Allomancer.
- A **Coinshot** (steel) Pushing the same object opposes your Pull, according to their weight and the force they apply.
- Metal inside a living body cannot normally be Pulled.
- Pulling something heavier than you drags you toward it instead, unless you are braced or anchored.

{{note

| | |
|---|---|
| **Base burn (1 ch/minute)** | See metal lines within 200 ft; 750 N Pull pool against metal within 120 ft |
| **Per flare charge** | +750 N to the round's pool, up to your level in charges |
| **Signature uses** | Disarm a foe, grapnel to an anchor (Table B), drive a projectile (Table E) |

}}

\page
## Force Tables

These tables serve both Steel and Iron. Read weight against charges; there is no math at the table.

## Steel & Iron Force & Damage Lookup Tables

Table-driven knockback, launch, and damage for Steelpushing and Ironpulling. No arbitrary caps; everything is simulated physics, pre-baked so you just read a value.

**How force works.** Burning metal gives you a **force pool** for the round:

> **Force pool (Newtons) = 750 × charges burned this round.**

You distribute that pool freely across your Pushes, Pulls, and driven coins. Every table below is keyed by the **force applied to a given target or coin**, so you never convert back to charges: split your pool into Newtons, then read each result directly.

| Charges | 1 | 2 | 3 | 5 | 10 | 20 |
|---|---|---|---|---|---|---|
| Force pool (N) | 750 | 1,500 | 2,250 | 3,750 | 7,500 | 15,000 |

> **Baked-in assumptions:** Heavy drag; knockback uses a 0.5 second shove, launch a 1.0 second committed push. Sustaining a push longer sends things much farther; simulate for chasm-jumps or odd cases. `FORCE_PER_CHARGE` (750 N) and `JOULES_PER_D6` (2,500) are the tuning knobs.

---

{{tableGroup

### Table B. Self-launch off an anchor (feet)

Push off an anchored or immovable metal. Lighter flyers go farther (`a = F/m`).

| Flyer weight | 750 N | 1,500 N | 2,250 N | 3,750 N | 7,500 N |
|---|---|---|---|---|---|
| 90 lb | 60 | 182 | 284 | 427 | 618 |
| 120 lb | 33 | 131 | 234 | 400 | 645 |
| 180 lb | 11 | 65 | 141 | 306 | 623 |
| 300 lb | 0 | 19 | 53 | 152 | 455 |
| 500 lb (koloss) | 0 | 3 | 14 | 54 | 225 |

}}

{{tableGroup

### Table C. Knockback of a target (feet)

Force applied to one target (pusher braced, so the full force drives the target). Heavier targets move less; `0` means their footing holds. If neither body is braced, the push also recoils the pusher, split by their relative weights.

| Target weight | 750 N | 1,500 N | 2,250 N | 3,750 N | 7,500 N |
|---|---|---|---|---|---|
| 90 lb (small) | 18 | 70 | 132 | 246 | 438 |
| 180 lb (medium) | 3 | 18 | 43 | 115 | 327 |
| 300 lb (large) | 0 | 5 | 14 | 44 | 171 |
| 600 lb (huge) | 0 | 0 | 2 | 9 | 45 |

}}

{{tableGroup

### Table D. Impact damage from a slam (bodies and large objects)

Damage from a body or sizeable object slammed into a hard surface, tied to impact energy: **damage = ½·m·v², at 1d6 per 2,500 J**, anchored so a person hitting at a 10-foot-fall speed is about 1d6, matching falling damage. No cap.

| Object (mass) | 33 ft/s | 66 ft/s | 98 ft/s | 148 ft/s | 197 ft/s |
|---|---|---|---|---|---|
| brick (2 kg) | ~0 | 0.2d6 | 0.4d6 | 0.8d6 | 1.4d6 |
| person (80 kg) | 1.6d6 | 6.4d6 | 14d6 | 32d6 | 58d6 |
| koloss (300 kg) | 6d6 | 24d6 | 54d6 | 122d6 | 216d6 |

}}

Round the die count to the nearest whole die in play. Read an object's speed from Table B or C, then its damage here.

{{tableGroup

### Table E. Driven coin or projectile damage (by force)

A Steelpushed coin, nail, or spike acts like a fired round; its lethality is the push **force** behind a tiny point, not its kinetic energy. Read damage directly from the force applied to that coin.

| Force behind the coin | Damage (piercing) | Real-weapon feel |
|---|---|---|
| up to 1,000 N | 1d6 | shortbow |
| 1,000 to 1,750 N | 1d8 | crossbow |
| 1,750 to 2,750 N | 1d10 | |
| 2,750 to 4,500 N | 1d12 | |
| 4,500 to 6,500 N | 2d6 | 9mm pistol |
| 6,500 to 8,500 N | 2d8 | |
| 8,500 to 10,500 N | 2d10 | rifle |
| 10,500 to 13,000 N | 3d8 | |
| 13,000 to 17,500 N | 5d6 | |
| 17,500 to 22,000 N | 4d10 |.50 cal |
| each +5,000 N above | +1d10 | |

}}

To hit, add your **proficiency bonus + Constitution modifier**; damage is **piercing**; range **60/240 ft**. Split your force pool across several coins to fire a volley, reading each coin's damage from the force you put behind it. An aluminum coin cannot be driven. Optional: at 4,500 N (9mm) or higher, a coin ignores the AC bonus of nonmagical armor.

---

\page

## Tin: Tineye

*The world sharpens. A Tineye hears a heartbeat through a wall and sees the assassin's shadow before the candle gutters, yet a sudden torch can bring them to their knees.*

**Bloodline** Physical Misting · **Metal** Tin (pure) · **Direction** Internal Pull · **Tempo** Minute (sustained buff) · **Charges/gram** 60

An Allomancer burning tin, called a **Tineye**, has dramatically heightened senses. Tin burns on the minute tempo: the effect runs for as long as it is lit, and grows sharper the more charges you feed it each minute.

### Base Burn

While you burn tin, at a base rate of 1 charge per minute, your five senses sharpen.

- You gain advantage on Wisdom (Perception) checks and a +5 bonus to passive Perception.
- You gain darkvision out to 30 feet. You see in dim light and in shades of gray in nonmagical darkness, but not in total or magical darkness, because tin amplifies existing light rather than creating sight where there is none.
- You pick out fine detail and faint sounds at a distance, and you notice things an ordinary person would miss, such as a tripwire's tension or the scent of a poison.

{{tableGroup

### Flaring

Each extra charge you burn in a minute, up to a number equal to your level, intensifies your senses for that minute.

| Extra charges | Added effect (cumulative) |
|---|---|
| +1 to 2 | Darkvision range increases to 60 ft, and you have advantage on tracking and on finding hidden creatures or objects by sense. |
| +3 to 4 | You gain blindsight out to 10 feet, a touch-and-vibration tremor sense, and you cannot be surprised while conscious and burning tin. |
| +5 or more | Your blindsight extends to 30 feet, and you sense minute changes such as a held breath or a drawn bowstring. The DM may grant advantage on initiative and on reading a creature's intentions. |

}}

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap grants **+1 to Perception checks** and **+10 feet** to the range at which any one sense reaches.

**Light becomes the limit before the senses do.** Sensitivity multiplies what reaches you, and ordinary rooms are brighter than they feel. Past roughly a hundredfold, a lit interior is as painful as staring at the sun and you are effectively **blinded** in any lit space, working in darkness or behind smoked glass until you stop. This is why tin savants are found hooded at noon, and it is the same effect as Sensory Overload below, arrived at from the other direction.

### Sensory Overload

Heightened senses cut both ways. While you burn tin, a sudden bright light or loud noise, such as a *light* spell flaring, a thunderous boom, or a flash pellet, forces a Constitution saving throw against a DC set by the source, or DC 13 by default.

- **Failure.** You are Stunned until the end of your next turn, or Blinded or Deafened depending on the source, as the input overwhelms you. You have disadvantage on this save if you are flaring 3 or more charges.
- **Success.** You shrug it off but have disadvantage on Perception checks until the end of your next turn.

A Tineye can snuff their tin as a free reaction to brace against an anticipated flash, though the sudden dulling of their senses is disorienting.

### Interactions & counterplay

- Tin only amplifies observable input. It never reveals what makes no impression on the senses; an invisible creature gives off no light, so tin alone will not let you see one, though you may still hear or feel it.
- Flaring tin can shock you alert, ending the effects of drowsiness, fatigue, or a drug, as a free action once per short rest.

{{note

| | |
|---|---|
| **Base burn (1 ch/minute)** | Advantage on Perception, +5 passive Perception, darkvision 30 ft |
| **Flaring** | Extends darkvision, adds blindsight and tremor sense, guards against surprise |
| **Sensory Overload** | Sudden bright light or loud sound forces a Con save or you are Stunned |

}}

\page

## Pewter: Thug (Pewterarm)

*A Thug shrugs off a crossbow bolt, rips a door from its hinges, and keeps running, until the pewter putters out and every wound they ignored arrives at once.*

**Bloodline** Physical Misting · **Metal** Pewter (91% tin, 9% lead) · **Direction** Internal Push · **Tempo** Round (intense, drains fast) · **Charges/gram** 50

An Allomancer burning pewter, called a **Thug** or **Pewterarm**, has vastly enhanced physical power and toughness. Pewter burns on the round tempo, one charge every round even at base burn, so it drains fast. Two things are unique to it: **Pewter Drag**, which lets you set wounds aside, and **the Crash**, which makes you pay for them later.

### Base Burn

While you burn pewter, at a base rate of 1 charge per round, you gain the following benefits.

- You have advantage on Strength, Dexterity, and Constitution checks and saving throws.
- Your walking speed increases by 10 feet.
- You have a +2 bonus to melee and unarmed damage rolls.
- You have advantage on grapple and shove checks and count as one size larger for carrying capacity.
- Your body toughens against force. Your **force tolerance doubles**, the amount of force you can safely apply to or endure against your own frame, chiefly the recoil of Steelpushing and Ironpulling something immovable (see The force turns on you). It rises further as you flare.
- You ignore the penalties of Exhaustion.

### Flaring

Each extra charge you burn in a round, up to a number equal to your level, drives your body further past its natural limits. This scaling has no fixed ceiling; what lets you survive it is your Pewter Drag capacity, below, which grows with every charge you burn.

- Each extra charge grants a further +2 bonus to melee and unarmed damage and increases your speed by 5 feet.
- Each extra charge grants **5 temporary hit points**, which last while you burn and are lost when you stop. This is what a pewter burner's famous toughness is: not an immunity, but a body that keeps going through what should have stopped it.
- While you flare 5 or more charges, once on each of your turns you may treat a Strength check or a shove as though your Strength score were 30, and you can jump twice your normal distance.
- At the **surge tier** (20 or more charges in a round; see the core rules, or half that for a pewter savant, or any duralumin detonation), you reach legendary feats of might. You can shatter stone with a blow, tear a barred door from its frame, or strike hard enough to break bone and armor alike. Each charge beyond the threshold continues to add its damage and speed and to expand your Pewter Drag capacity.

{{tableGroup

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

| Per 2 charges past the cap | |
|---|---|
| **Strength score** | **+1**, and this **ignores the ceiling of 30** that otherwise binds an ability score. Nothing else in these rules lifts that ceiling. |
| **Melee and unarmed damage** | +2, in addition to what the raised Strength modifier already gives. The flat bonus is the metal driving the blow; the score is what your body can hold and lift. Both are real, and for one round both apply. |
| **Speed** | +5 feet |
| **Temporary hit points** | +5 |
| **Launch G-ceiling** | +5 G, the acceleration your body can take from a Steelpush; see the Steel entry |

}}

A 5th-level Thug who detonates a 5 gram vial spends 250 charges, 245 of them past the cap: **Strength 132, +244 damage on top of the Strength modifier, 610 temporary hit points, and the strength to lift about two tons.** It lasts one round. Then the pewter is gone, the temporary hit points with it, and every wound you did not feel arrives at once.

### Pewter Drag

Pewter lets you keep fighting through wounds that would fell anyone else, at a price you pay later. When you take damage while burning pewter, you may store some of it as drag rather than losing hit points.

- You can hold an amount of drag equal to the charges you have burned this round times your level.
- Stored drag does nothing to you while you keep burning pewter. Damage beyond your drag capacity is taken as normal.
- While you have pewter to burn, Hit Dice spent on a short rest restore the maximum, and you have advantage on death saving throws.

\page
### The Crash

When your pewter runs out, or you stop burning it, whether by choice or by spending your last charge mid-fight, every wound you set aside arrives at once. You immediately take all stored drag as a single hit of damage, and you gain one level of Exhaustion. If you were flaring 6 or more charges when the pewter ended, you gain two levels of Exhaustion instead.

A Thug who leans on pewter and burns their last charge in a fight is suddenly, mortally vulnerable.

### Interactions & counterplay

- Pewter is a round-tempo metal that drains fast, one charge per round even at base burn, so a long fight is a real strain on your reserve. Plan your carry using Carrying & the 24 hour rule.
- A Leecher (chromium) or an aluminum burn can wipe your reserve in an instant, forcing an immediate Crash.

{{note

| | |
|---|---|
| **Base burn (1 ch/round)** | Advantage on Str, Dex, Con; +10 ft speed; +2 melee; grapple and shove edge |
| **Flaring** | Scales damage, speed, and resistance with no fixed ceiling |
| **Pewter Drag** | Store damage now, capacity grows with charges times level |
| **The Crash** | Stored damage plus Exhaustion when your pewter ends |

}}

{{imageMaskCorner21,--offsetX:40%,--offsetY:-30%,--rotation:0
  ![Pewter: a Thug punching in a brawl](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/misting-pewter-thug.jpg?v=87e5e8e6){height:100%}
}}

\page

### Mental

*Four metals for the space between people, and for Allomancy itself.*

The Mental quadrant reaches minds rather than matter. Zinc and brass work outward on other people's emotions, riding a mood up into fury or damping it down into calm, which makes them the metals of the negotiation, the con, and the panicked crowd. Copper and bronze turn the same sensitivity inward on the art itself: one hides your burning from anyone listening, the other lets you do the listening. Little here wins a fight outright. Most of it decides whether there is a fight.

::::

## Zinc: Rioter

*A Rioter says nothing, yet the crowd's unease curdles into panic and the calm room turns to a brawl.*

**Bloodline** Mental Misting · **Metal** Zinc (pure) · **Direction** External Pull · **Tempo** Minute · **Charges/gram** 20

An Allomancer burning zinc, called a **Rioter**, can **inflame** the emotions of those around them. Rioting is not mind control and it cannot read minds or plant thoughts; it only stirs feelings a creature could already have.

### Base Burn

While you burn zinc, at a base rate of 1 charge per minute, you continuously emit an emotional pulse. You do not spend an action to send it. The pulse radiates while you burn and renews itself each round on its own. On each of your turns, without using an action, you may re-aim it.

A pulse fills either a 30-foot cone or a 15-foot-radius sphere centered on you, reaching only creatures you can see. Stirring **every** emotion at once is easier than picking out a single one, so by default the pulse inflames all of a creature's feelings together. When a creature first enters the pulse, and again at the start of each of its turns while it remains inside, it makes a Wisdom saving throw against your Allomancy save DC. On a failed save, the creature is overwhelmed by surging emotion until the start of its next turn: it has disadvantage on attack rolls and ability checks, and the DM may have it act on whatever it feels most strongly, lashing out or fleeing.

### Flaring

Each extra charge you burn, up to a number equal to your level, sustains one more effect while you burn, chosen and adjustable on your turn.

- **Isolate an emotion.** Differentiating one feeling from the rest is the harder, more skilled use of the art. Spend 1 charge to single out a specific emotion and inflame only it, applying a precise effect from the Possible Effects table instead of the blanket surge. You can also reach an emotion the target only faintly feels, swelling a seed into a surge.
- **Strengthen a pulse.** Add 15 feet to its range, and impose disadvantage on its save or add 1 to the DC.
- **Add a pulse.** Emit another pulse in a different direction. With enough charges you can single out one distant creature or sweep an entire street.

Spending a second charge on a pulse also lets you **exclude chosen allies** from it.

{{tableGroup

#### Possible effects (isolated emotion)

The effect of a single inflamed emotion is up to the DM and depends on what the creature already feels. Typical examples:

| Emotion | Possible effect on a failed save |
|---|---|
| Fear | Frightened of a source you designate. |
| Rage | Must move toward and attack the nearest creature it can reach. |
| Despair | Disadvantage on attack rolls and ability checks. |
| Zeal | Immune to the Frightened condition and advantage on saves against being Charmed. |

}}

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap adds **30 feet** to a pulse's range and **+1** to its save DC, or emits one more pulse.

#### Against a spiked creature

Spikes are the handle by which emotional Allomancy commands a koloss, and they answer to anyone strong enough to take hold. A **duralumin detonation** aimed at a creature bearing Hemalurgic spikes does not sway a mood. **It takes the creature.**

- Against a **koloss**, or anything bearing a single spike, this is seizure rather than influence: it obeys you while you sustain the burn, and is free the moment the metal runs out. This is how one Soother turns a war band, and it is why the Lord Ruler never let a koloss near a Soother who was not his.
- Against an **Inquisitor**, whose spikes are many and whose will is its own, it is a contest: make an Allomancy check against its Wisdom saving throw. Win and you hold it for the round. Lose and it knows precisely who reached for it.
- A creature with **no spikes** is unaffected by any of this. There is nothing to take hold of.

\page
### Interactions & counterplay

- Rioting is blocked by **aluminum**: a creature wearing aluminum around the head, standing in an aluminum-lined room, or holding aluminum against your chest is immune.
- A creature burning **copper** (copper) is immune to Rioting.
- You must be able to **see** into the area; pulses do not pass through total cover or around corners.

{{note

| | |
|---|---|
| **Base burn (1 ch/minute)** | Continuous pulse; inflame all emotions at once (blanket), Wis save each turn |
| **Flaring** | Isolate a single emotion for a precise effect, strengthen, or add pulses; exclude allies |

}}

\page

## Brass: Soother

*A Soother's presence is a quiet balm. Anger cools, suspicion fades, and a frightened guard finds, without knowing why, that they trust the stranger at the gate.*

**Bloodline** Mental Misting · **Metal** Brass (about 75% copper, 25% zinc) · **Direction** External Push · **Tempo** Minute · **Charges/gram** 20

An Allomancer burning brass, called a **Soother**, can **dampen** the emotions of those around them. Soothing is the mirror of Rioting. It is not mind control and cannot read minds; it only quiets feelings a creature already has.

### Base Burn

While you burn brass, at a base rate of 1 charge per minute, you continuously emit a soothing pulse. You do not spend an action to send it. The pulse radiates while you burn and renews itself each round on its own. On each of your turns, without using an action, you may re-aim it.

A pulse fills either a 30-foot cone or a 15-foot-radius sphere centered on you, reaching only creatures you can see. Quieting **every** emotion at once is easier than picking out a single one, so by default the pulse dampens all of a creature's feelings together. When a creature first enters the pulse, and again at the start of each of its turns while it remains inside, it makes a Wisdom saving throw against your Allomancy save DC. On a failed save, the creature is becalmed until the start of its next turn: it has disadvantage on attack rolls, cannot take reactions, and is disinclined to violence, taking no hostile action unless it or an ally is harmed. A heavier, sustained soothe can leave a crowd listless and apathetic, as the Lord Ruler once quieted whole squares.

### Flaring

Each extra charge you burn, up to a number equal to your level, sustains one more effect while you burn, chosen and adjustable on your turn.

- **Isolate an emotion.** Differentiating one feeling from the rest is the harder, more skilled use of the art. Spend 1 charge to single out a specific emotion and dampen only it, applying a precise effect from the Possible Effects table instead of the blanket calm.
- **Strengthen a pulse.** Add 15 feet to its range, and impose disadvantage on its save or add 1 to the DC. Enough charges press even strong emotion down toward apathy.
- **Add a pulse.** Emit another pulse in a different direction.

Spending a second charge on a pulse also lets you **exclude chosen allies** from it.

{{tableGroup

#### Possible effects (isolated emotion)

The effect of a single dampened emotion is up to the DM and depends on what the creature already feels. Typical examples:

| Emotion | Possible effect on a failed save |
|---|---|
| Fear | The Frightened condition ends, and the creature cannot be Frightened for the duration. |
| Aggression | The creature cannot take the Attack action unless it or an ally has been attacked since its last turn. |
| Suspicion | In a social situation, the creature's attitude toward you improves by one step, from hostile to indifferent, or indifferent to friendly. |
| Resolve | The creature has disadvantage on saving throws against being Frightened or Charmed. |

}}

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap adds **30 feet** to a pulse's range and **+1** to its save DC, or emits one more pulse.

#### Against a spiked creature

Spikes are the handle by which emotional Allomancy commands a koloss, and they answer to anyone strong enough to take hold. A **duralumin detonation** aimed at a creature bearing Hemalurgic spikes does not sway a mood. **It takes the creature.**

- Against a **koloss**, or anything bearing a single spike, this is seizure rather than influence: it obeys you while you sustain the burn, and is free the moment the metal runs out. This is how one Soother turns a war band, and it is why the Lord Ruler never let a koloss near a Soother who was not his.
- Against an **Inquisitor**, whose spikes are many and whose will is its own, it is a contest: make an Allomancy check against its Wisdom saving throw. Win and you hold it for the round. Lose and it knows precisely who reached for it.
- A creature with **no spikes** is unaffected by any of this. There is nothing to take hold of.

### Interactions & counterplay

- Soothing is blocked by **aluminum**: a creature wearing aluminum around the head, standing in an aluminum-lined room, or holding aluminum against your chest is immune.
- A creature burning **copper** (copper) is immune to Soothing.
- You must be able to **see** into the area; pulses do not pass through total cover or around corners.

\page

{{note

| | |
|---|---|
| **Base burn (1 ch/minute)** | Continuous pulse; dampen all emotions at once (blanket), Wis save each turn |
| **Flaring** | Isolate a single emotion for a precise effect, strengthen toward apathy, or add pulses; exclude allies |

}}

\page

## Copper: Smoker

*Around a Smoker hangs an unseen quiet. Within it, Allomancy leaves no ripple, and a Seeker's questing pulses find nothing at all.*

**Bloodline** Mental Misting · **Metal** Copper (pure) · **Direction** Internal Pull · **Tempo** Minute · **Charges/gram** 40

An Allomancer burning copper, called a **Smoker**, is shielded from emotional Allomancy and raises a **coppercloud** that hides the use of magic from outside detection.

### Base Burn

While you burn copper, at a base rate of 1 charge per minute, you gain the following.

**Unshakable Mind.** You are immune to emotional Allomancy (Rioting and Soothing) and cannot be Charmed by magical means.

**Coppercloud.** An invisible bubble with a 10-foot radius surrounds you and moves with you. Any Allomancy, Feruchemy, or other Investiture or magic used by a creature inside the cloud cannot be detected from outside it, including by a Seeker or by effects such as *detect magic*. This is not physical invisibility; it hides magical activity only. A creature inside the cloud likewise cannot sense magical activity that occurs outside it.

### Flaring

Each extra charge you burn in a minute, up to a number equal to your level, increases the coppercloud's **radius by 10 feet** and its **strength**. The cloud's strength sets the DC to pierce it, equal to your Allomancy save DC plus 1 for each charge flared. Multiple Smokers who overlap their clouds add their strengths together.

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap adds **20 feet** to the coppercloud's radius and **+1** to the DC to pierce it.

### Piercing a coppercloud

A coppercloud normally cannot be seen through by any sensing power. It can be pierced only by:

- a **Seeker who is a bronze savant** (see Savants),
- a Seeker who **flares bronze together with duralumin**,
- a Seeker carrying a **bronze Hemalurgic spike**, effectively burning double bronze, or
- a far stronger Seeker, such as one enhanced by lerasium.

A creature able to pierce the cloud must succeed on a Wisdom saving throw against the cloud's strength to sense what happens inside.

### Interactions & counterplay

- Copper does not grant **others** in the cloud immunity to emotional Allomancy; only the Smoker is shielded.
- A coppercloud hides magical activity but not the creatures themselves, and it does not block sound, sight, or physical searches.
- Aluminum still ends or wipes powers as normal; copper does not protect metal reserves from a Leecher.
- At a D&D table, the cloud hides everyone inside from **magical detection and divination** (*detect magic*, *scrying*, *locate creature*), and the Smoker alone resists mind-reading. See The Metallic Arts and the Weave.

{{note

| | |
|---|---|
| **Base burn (1 ch/minute)** | Immune to emotional Allomancy and Charm; 10-ft coppercloud hides magic use |
| **Flaring** | +10 ft radius and greater cloud strength per charge |
| **Piercing** | Only a bronze savant, double bronze, or bronze plus duralumin, versus the cloud's strength |

}}

{{imageMaskCorner21,--offsetX:50%,--offsetY:-50%,--rotation:0
  ![Copper: a Smoker covering a room](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/misting-copper-smoker.jpg?v=14ed69bf){height:100%}
}}

\page

## Bronze: Seeker

*A Seeker hears what others cannot: the silent drumbeat of burning metal, and the tolling pulse of a spell being cast three rooms away.*

**Bloodline** Mental Misting · **Metal** Bronze (88% copper, 12% tin) · **Direction** Internal Push · **Tempo** Minute · **Charges/gram** 30

An Allomancer burning bronze, called a **Seeker**, can sense the pulses given off by Allomancy and by other uses of magic.

### Base Burn

While you burn bronze, at a base rate of 1 charge per minute, you sense magical pulses.

**Seeking.** You are aware of any creature within 60 feet that is burning a metal, tapping a metalmind, or casting a spell, and you know the rough direction of each. You have advantage on Wisdom (Perception) and Wisdom (Insight) checks to notice such a power being used, and you cannot be surprised by a creature that is using Allomancy, Feruchemy, or magic within range.

{{tableGroup

### Flaring

Each extra charge you burn in a minute, up to a number equal to your level, increases both the **range** of your sense (by 60 feet) and its **fidelity**, unlocking finer detail as you invest more.

| Extra charges | Added detail |
|---|---|
| +1 to 2 | Exact direction and distance to each source, and its precise location. |
| +3 to 4 | The kind of power in use: which metal is burned, or that a spell is being cast and its relative power. |
| +5 or more | Fine detail, including whether an object is magical and roughly how strongly, similar to *detect magic*. |

}}

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap adds **120 feet** of range and **+1** to the DC to read through a coppercloud.

### Interactions & counterplay

- A **coppercloud** (copper) blocks Seeking entirely; you sense nothing that happens inside one, unless you can pierce it. See Piercing a coppercloud.
- Other concealment or suppression magic hinders your sense, at the DM's discretion, though you can usually still tell that magic of some kind is being masked.
- A Seeker who burns bronze constantly may become a **bronze savant** (Savants), gaining greater range and the ability to pierce copperclouds.
- At a D&D table, bronze senses **ordinary spellcasting and magic** as readily as Allomancy (a spell reads as the Investiture it is), but only while the power is *active*; dormant magic is quiet. See The Metallic Arts and the Weave.

{{note

| | |
|---|---|
| **Base burn (1 ch/minute)** | Sense burning metal, metalminds, and spellcasting within 60 ft; no surprise by them |
| **Flaring** | +60 ft range per charge, plus rising detail (direction, type, magic sense) |
| **Blocked by** | Copperclouds, unless you can pierce them |

}}

{{imageMaskCorner21,--offsetX:50%,--offsetY:-30%,--rotation:0
  ![Bronze: a Seeker](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/misting-bronze-seeker.jpg?v=82366133){height:100%}
}}

\page

### Enhancement

*Four metals that do nothing on their own.*

Every metal in the Enhancement quadrant is a multiplier or an eraser of somebody's power, never a power in itself. Aluminum and duralumin act on the Allomancer burning them, wiping their own reserves clean or detonating them all at once. Chromium and nicrosil reach out and do the same to someone else. Choosing from this quadrant is choosing to be the answer to another Allomancer, which is quiet at a table with no rival Mistings in it and decisive at one full of them.

::::

## Aluminum: Aluminum Gnat

*The metal that unmakes metal. An Allomancer who burns it feels their power simply vanish.*

**Bloodline** Enhancement Misting · **Metal** Aluminum (pure) · **Direction** Internal Pull · **Tempo** Instant · **Charges/gram** 10

An Allomancer burning aluminum instantly clears their own Allomantic reserves. On its own this does almost nothing, which is why a Misting who can burn only aluminum is mocked as an **Aluminum Gnat**.

> **Gnat.** With no other metal to clear, an Aluminum Gnat's power turns on nothing. Aluminum matters to a Mistborn, who has reserves worth clearing, and to anyone holding aluminum as a defense. As a lone bloodline it is nearly useless.

### Base Burn

Burning a charge of aluminum is instantaneous. As a free action, on your turn or in response to another creature's action, you burn one charge to **metabolize every metal in your body at once**. All metals you are burning end, your reserves empty, and the aluminum is consumed with them.

This is different from simply extinguishing a burn. Stopping a burn is free and leaves the metal in your body, still there to be re-lit or detonated. Aluminum **removes the metal entirely**, leaving you with nothing to draw on.

Emptying your reserves is the work of a **single charge**. Beyond that, aluminum can begin to **cleanse your own spirit** of foreign Investiture: with one charge you may end a *minor* ongoing magical or Invested effect on yourself, making a Constitution saving throw against it if it allows one.

### Flaring

Where clearing your metals is binary, cleansing your spirit **scales with the charges you pour into a single burn**, up to a flare cap equal to your level. The more you spend at once, the stronger the Investiture you can scour away.

- Treat the total charges spent as the **strength of the cleanse**. You may end an ongoing magical or Invested effect on yourself whose strength (its spell level, or a tier the DM sets) is no greater than the charges spent. Because you are scouring your *own* spirit by choice, no saving throw resists you.
- This can strip clinging foreign Investiture as well as spells: a measure of another's power that has taken hold of you (borrowed Stormlight, a lodged Breath, a curse, an enemy's ongoing spell) can be burned out of your spirit if you spend enough.
- **At the surge tier** (see the core rules), or as an aluminum savant (whose cap is doubled), you can **cleanse even powerful, Shard-level Investiture** (up to a 9th-level or legendary effect) from your own spirit, the rarest and most coveted use of the metal.

You still cannot reach *another* creature's Investiture with aluminum; it acts only on yourself. To strip someone else, see Chromium (Leecher). At a D&D table this is how aluminum ends spells and curses on you; full rules in The Metallic Arts and the Weave.

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap adds **+1** to the strength of the cleanse.

### Notable uses

- **Imprisonment and transport.** Because aluminum strips the metal itself, not just the burn, a captured Allomancer left with only aluminum can be made to empty their reserves, leaving them powerless. This was the metal's chief use in the Final Empire.
- **Deception.** A Leecher or Nicroburst can feel whether their touch actually drained or detonated anything. Emptying your reserves beforehand can convince them you were carrying no metal at all.

{{note

| | |
|---|---|
| **Base burn (instant, 1 ch)** | Free action: remove all your own metal, burning and unburned; may end a minor Invested effect on you |
| **Flaring** | Charges = strength of spiritual cleanse; higher-level effects and clinging Investiture (flare cap = level) |
| **Savant** | Cleanse even Shard-level Investiture from your own spirit |
| **Note** | An Aluminum Gnat can do almost nothing with the reserve-clear alone |

}}

\page

## Duralumin: Duralumin Gnat

*One breath of power spent all at once. A Coinshot who flares duralumin can hurl a carriage; a Thug can shatter a wall with a shoulder.*

**Bloodline** Enhancement Misting · **Metal** Duralumin (96% aluminum, 4% copper) · **Direction** Internal Push · **Tempo** Instant · **Charges/gram** 10

An Allomancer burning duralumin empties every other metal they are burning in a single, overwhelming instant. Like aluminum, it does nothing on its own, so a Misting who can burn only duralumin is a **Duralumin Gnat**.

> **Gnat.** Duralumin has no effect of its own; all of its power is borrowed from the metals it detonates. A Duralumin Gnat, burning duralumin alone, does nothing at all.

\column

### Base Burn

Burning a charge of duralumin is instantaneous. As a free action, you **consume every charge you currently hold of every other metal you are burning, all at once**, ignoring your per-round flare cap and any limit on how many charges you may burn in a round. Apply the full combined effect of all those charges this round. The metals are then spent and gone.

This is the single largest burst an Allomancer can produce, and it empties your reserves to do it.

{{wide

### Detonation by metal

A duralumin burst spends **your entire held reserve of that metal in one instant**, ignoring the flare cap. What that buys differs sharply by metal: some become overwhelming, some barely change, and a few do something they cannot otherwise do at all.

| Metal | What the detonation does |
|---|---|
| **Iron / Steel** | A single force pool equal to your whole reserve, spent this round or wasted. Read Tables B and C at the full combined force. The classic use: a Push no anchor survives. |
| **Tin** | Every sense at once, past what a body is meant to carry. In near-total deprivation you perceive what is hidden; in an ordinary room you may simply overwhelm yourself. See Sensory Overload. |
| **Pewter** | The legendary tier of might and endurance for the round. Shattered stone, torn doors, a fall that should have killed you. |
| **Zinc / Brass** | Every creature in range is swept by one overwhelming surge of feeling. A total soothe can leave a crowd standing catatonic; a total riot can start a massacre. |
| **Copper** | A coppercloud that briefly covers a district rather than a room. It does not become stronger, only vastly wider, and it collapses at once. |
| **Bronze** | You sense every source of power nearby at the same moment, and briefly hear straight through copperclouds. See Piercing a coppercloud. |
| **Aluminum** | Your reserves are already being consumed; aluminum adds only that the *scouring* is total. Nothing Invested that you were carrying internally survives it. |
| **Duralumin** | Nothing. Duralumin cannot detonate itself, and a reserve of it is simply spent. |
| **Chromium** | One touch strips a target's entire reserve to nothing, with no gradual drain and nothing left behind. This is how the Steel Ministry disarmed Allomancers. |
| **Nicrosil** | The target's burn is amplified to the same all-at-once extreme, using **their** reserve rather than yours. A gift or an execution, depending on what they are burning. |
| **Gold** | One vast, complete vision of the self you might have been, rather than a glimpse. Overwhelming, and remembered. |
| **Electrum** | Your own near future laid out at length instead of a heartbeat ahead. The advantage lasts the round and then is gone. |
| **Cadmium / Bendalloy** | The bubble's ratio becomes **2 plus twice your entire remaining reserve in charges**, for one round, after which the metal is gone and the bubble collapses. A Slider with 10 charges left buys their occupants 22 rounds inside a single round outside; a Pulser buys 22 rounds of the world passing while they take one. |
| **Atium / Malatium** | A god metal is not spent this way. The detonation consumes the reserve and grants a single round of the metal's effect at its fullest, which for atium means near-perfect foresight against everyone present at once. |

}}

\page
{{tableGroup

#### Feruchemy

Flaring duralumin lets the burst reach past Allomancy to **one non-Allomantic power you are using in the same instant**. Against Feruchemy that means a **tap**, and only a tap.

| What you are doing | What the burst does |
|---|---|
| **Tapping a metalmind** | The draw you would have spread over its duration is released **at once**, at that amplified intensity, and **that metalmind is emptied entirely** rather than drawn down by what you needed. |
| **One mind, not all of them** | The burst takes **the single metalmind you are tapping**, and stops there. It does not reach across to your other minds, even of the same metal: a Bloodmaker wearing five goldminds burns out one and still has four. This is the difference between Feruchemy and Allomancy under duralumin, where a reserve is one pool and all of it goes. |
| **Storing into a metalmind** | Nothing. Storing is a slow giving-up, not a draw, and there is nothing to release. |
| **Compounding** | The Compounded tap detonates as any tap does, which is the most dangerous version of this trick: a gold Compounder bursting a healing tap can undo grievous harm in a single round, and has nothing left afterward. |
| **An unsealed metalmind** | As any tap, but the reserve belongs to whoever filled it. Bursting someone else's bank empties it for them too. |

}}

**Spellcasting is not here.** A duralumin burst can maximize a spell you cast this turn, and that rule lives in The Metallic Arts and the Weave with the rest of the crossover layer, so a table playing without it never meets a rule it cannot use.

### Flaring

For the Allomantic detonation, a single charge is enough; it already burns *everything*. Flaring duralumin instead lets the burst reach **beyond Allomancy**, to other Investiture you are actively wielding in the same instant.

- The detonation can seize one form of **non-Allomantic Investiture you are using right now**: a **Feruchemical tap** (releasing a metalmind's draw in one amplified surge rather than over time), or, at a D&D table, **a spell you cast this turn**. A spell is **maximized** and may be upcast to the summed level of any spell slots you feed in; a concentration spell then ends. The full rules for spells live in The Metallic Arts and the Weave.
- **At the surge tier**, or as a duralumin savant (whose cap is doubled), you can burst even a **powerful external Investiture** (up to a 9th-level or legendary effect), wringing a single overwhelming moment from a source that would normally release its power slowly.
- As with the Allomantic burst, whatever you detonate is **spent** by it; a tap or a fed spell slot burst this way is consumed at once.

### Interactions & counterplay

- Duralumin detonates **your own** power. To force the same burst on another Allomancer, see Nicrosil (Nicroburst).
- Because it ignores the flare cap, duralumin is how an Allomancer briefly exceeds their normal per-round limits, at the cost of their entire reserve.
- **Time bubbles reach the same heights without duralumin.** Emotional Allomancy worked *inside your own* speed bubble can match a duralumin detonation: to the outside world a Rioter or Soother burning even one charge per round is burning as many charges per outside-round as the bubble's compression (a 16-to-1 bubble makes it 16), and the pulse can still be aimed without the usual disorientation of firing across a bubble's edge. See bendalloy.

{{note

| | |
|---|---|
| **Base burn (instant, 1 ch)** | Free action: burn all your other held charges at once, ignoring the flare cap |
| **Flaring** | Burst your own non-Allomantic Investiture: a Feruchemical tap, or a spell you cast (maximized + upcast to summed fed slots); flare cap = level |
| **Savant** | Burst even a powerful, Shard-level (9th-level/legendary) external Investiture |
| **Note** | A Duralumin Gnat can do nothing with this power alone |

}}

\page

## Chromium: Leecher

*A Leecher's touch is a sudden, sinking cold, and the power a rival was counting on is simply gone.*

**Bloodline** Enhancement Misting · **Metal** Chromium (pure) · **Direction** External Pull · **Tempo** Instant · **Charges/gram** 10

An Allomancer burning chromium, called a **Leecher**, wipes the Allomantic reserves of another person on touch. It is aluminum turned outward, forced upon someone else.

### Base Burn

Burning a charge of chromium is instantaneous and takes effect through touch. As an action, you reach out to touch a creature within your reach. If the creature is unwilling and aware of you, it makes a Dexterity saving throw against your Allomancy save DC to avoid your touch; on a success it evades you and the charge is not spent. A creature that is willing, surprised, or unaware that you are a Leecher is touched automatically, with no save. On a touch, you burn one charge of chromium and **wipe that creature's Allomantic reserves**: every metal it is burning ends immediately, and its stored charges are consumed. The target feels a deep, sudden cold as its power drains away.

A creature's ordinary Allomantic reserves are wiped by that single charge, unwilling and unstored alike.

### Flaring

Chromium reaches **past Allomancy** as you pour more into a single touch, up to a flare cap equal to your level. Where one charge empties an Allomancer, more charges let you drain **other forms of Investiture** on contact, their strength setting how much you can snuff.

- With enough charges you can, on a touch: snuff a measure of a target's **Breath** or **Stormlight**; **interrupt a Feruchemist who is tapping a metalmind**, cutting the draw; drain the animating Investiture of a **Lifeless**; keep a Shardbearer from **summoning their Blade** for the moment; or silence an **Invested weapon**. The charges you spend must overcome the strength of the Investiture; the flare cap is your level.
- **At the surge tier**, or as a chromium savant (whose cap is doubled), you can tear at even **powerful, Shard-level Investiture**, the reason Leechers are feared far beyond a duel of Allomancers.
- As always, an unwilling and aware target still gets a Dexterity save to avoid the touch entirely; no touch, no drain. Chromium reaches only what is **live**: it never drains a caster's spell slots or capacity, only the magic actually in use. Full rules for draining spells and magic items are in The Metallic Arts and the Weave.

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap adds **+1** to the strength of the drain.

### Interactions & counterplay

- A target who burns **aluminum** in response can clear their own reserves first, denying you the satisfaction but ending their power all the same.
- Chromium wipes reserves; it does not prevent the target from ingesting and burning fresh metal afterward.
- To empty **your own** reserves instead, see Aluminum.

{{note

| | |
|---|---|
| **Base burn (instant, 1 ch)** | Action, touch (Dex save to avoid; auto if willing or oblivious): wipe the target's metals and reserves |
| **Flaring** | Extra charges drain other Investiture on touch (Breath, Stormlight, a Feruchemist's tap, Lifeless, Shardblade summon, Invested weapons); flare cap = level |
| **Savant** | Tear at even Shard-level Investiture |

}}

\page

## Nicrosil: Nicroburst

*A Nicroburst lends no power of their own. They lay a hand on an ally, and that ally's Allomancy erupts.*

**Bloodline** Enhancement Misting · **Metal** Nicrosil (85% tin, 15% chromium) · **Direction** External Push · **Tempo** Instant · **Charges/gram** 10

An Allomancer burning nicrosil, called a **Nicroburst**, triggers a duralumin-like detonation in another Allomancer on touch. It is duralumin turned outward.

### Base Burn

Burning a charge of nicrosil is instantaneous and takes effect through touch. As an action, you reach out to touch a creature within your reach. If the creature is unwilling and aware of you, it makes a Dexterity saving throw against your Allomancy save DC to avoid your touch; on a success it evades you and the charge is not spent. A creature that is willing, surprised, or unaware that you are a Nicroburst is touched automatically, with no save. On a touch, you burn one charge of nicrosil, and the target **instantly consumes every charge of each metal it is currently burning, all at once**, exactly as though it had burned duralumin. The target applies the full combined effect this round, then those metals are spent.

Used on an ally, this is a way to unleash their greatest burst on your action rather than theirs. Used on an enemy, it can force them to blow their whole reserve at the wrong moment.

### Flaring

For the Allomantic detonation, one charge suffices. Flaring nicrosil, like flaring duralumin, lets the burst reach **beyond Allomancy**, to other Investiture the target is wielding, up to a flare cap equal to your level.

- On a **willing ally**, you seize one form of **non-Allomantic Investiture they are using**, a **Feruchemical tap** or a spell they cast, exactly as duralumin does for oneself (a spell maximized and upcast by the slots they feed).
- On an **unwilling caster or Feruchemist**, you force them to **expend Investiture at the worst moment**, wasting an active spell or tap and forcing extra spell slots. Because that power is part of them, they make a **Constitution save** to protect half of it (their Allomantic metal, being external, is taken with no such save). Full rules in The Metallic Arts and the Weave.
- **At the surge tier**, or as a nicrosil savant (whose cap is doubled), you can reach even a **powerful, Shard-level Investiture** (up to a 9th-level or legendary effect) in the one you touch.

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap adds **+1** to the strength of the burst you grant or force.

### Interactions & counterplay

- Nicrosil only detonates power the target is **actively using**; against an Allomancer burning nothing and tapping nothing, it does nothing.
- To detonate **your own** metals, see duralumin.
- Nicrosil has deeper Feruchemical and cosmere uses tied to Investiture itself; those are out of scope for this bloodline and belong to Feruchemical nicrosil.

{{note

| | |
|---|---|
| **Base burn (instant, 1 ch)** | Action, touch (Dex save to avoid; auto if willing or oblivious): target detonates all its burning metals at once, as duralumin |
| **Flaring** | Burst the target's non-Allomantic Investiture (a Feruchemical tap, or a spell they cast); willing = empower, unwilling = force wasteful expenditure (Con save protects half); flare cap = level |
| **Savant** | Reach even a powerful, Shard-level (9th-level/legendary) Investiture in the one you touch |

}}

\page

### Temporal

*Four metals for time, which is the most expensive thing to spend.*

The Temporal quadrant buys knowledge of when, or command of it. Gold and electrum turn inward and show the burner a self they might have been or are about to become, which is information rather than force, and often unwelcome information. Cadmium and bendalloy turn outward and bend the rate of time itself inside a fixed bubble, letting a crew take four rounds while the world takes one, or strand a pursuer in slowed treacle. These metals reshape encounters rather than winning them, and they are the ones most likely to make a DM rethink a scene.

::::

## Gold: Augur

*An Augur looks into gold and meets a stranger wearing their own face: the person they might have been, had they chosen differently.*

**Bloodline** Temporal Misting · **Metal** Gold (pure) · **Direction** Internal Pull · **Tempo** Minute · **Charges/gram** 10

An Allomancer burning gold, called an **Augur**, sees a **gold shadow** of who they could have been. Like aluminum and duralumin, gold offers little of practical use, and an Augur who can burn only gold is nearly as limited as a Gnat.

### Base Burn

While you burn gold, at a base rate of 1 charge per minute, a translucent shadow of an alternate self appears near you, showing a life shaped by choices you did not make. You can see through both sets of eyes and hear both sets of thoughts at once. The image differs each time you burn, shifting with your present circumstances.

The experience is disorienting and often distressing, and it grants almost no advantage in the moment. Its worth is introspective. The DM may allow an Augur to glimpse the truth of a past decision, or grant advantage on a Wisdom saving throw against an effect that would rewrite the Augur's memories or identity, since they hold their own alternate selves clearly in mind.

Touching the gold shadow deepens the vision into the full weight of a life unlived, which is more distressing still and offers no further benefit.

### Flaring

Flaring does little. Burning more charges sharpens and prolongs the vision but grants no greater power, and this holds **past the flare cap as well**. A duralumin detonation of gold buys one vast and complete vision of the self you might have been rather than a glimpse, and nothing more. Some things do not become truer for being seen harder.

### Interactions & counterplay

- A gold shadow changes if the Augur has been altered by identity-shaping magic, such as a Forgery, reflecting the altered self.
- Gold is a poor combat metal. It is included for completeness and for the rare campaign that turns on who a character might have become.

{{note

| | |
|---|---|
| **Base burn (1 ch/minute)** | See a gold shadow of an alternate self; mostly introspective, little combat use |
| **Flaring** | Sharpens the vision; no greater power |
| **Note** | One of the weakest single bloodlines, on the level of the Gnats |

}}

\page

## Electrum: Oracle

*An Oracle sees a heartbeat ahead: a shadow of themselves stepping into the next moment, so nothing can truly take them by surprise.*

**Bloodline** Temporal Misting · **Metal** Electrum (about 45% gold, 55% silver) · **Direction** Internal Push · **Tempo** Minute · **Charges/gram** 10

An Allomancer burning electrum, called an **Oracle**, sees a few seconds of their **own** immediate future. It is often called poor man's atium, for it guards its user without granting atium's full command of another's fate.

### Base Burn

While you burn electrum, at a base rate of 1 charge per minute, you see a shadow of yourself roughly **3 seconds** into your own future, showing how you are about to move and react.

- You cannot be surprised.
- You have advantage on initiative.
- You are immune to having your future read by another creature's Allomancy. An enemy burning **atium** against you sees your atium shadow split and blur, and cannot predict your actions. The blinding runs both ways; see Interactions below.

{{tableGroup

### Flaring

Each extra charge you burn in a minute, up to a number equal to your level, pushes your foresight further ahead, about **3 seconds per charge**, and lets you act on what you see.

| Extra charges | Foresight | Added benefit |
|---|---|---|
| +1 to 2 | 6 to 9 seconds | You have advantage on Dexterity saving throws. |
| +3 to 4 | 12 to 15 seconds | Once on each of your turns, when a creature you can see attacks you, you can impose disadvantage on that attack roll as you slip aside a step early. |
| +5 or more | 18 seconds or more | Attackers you can see have disadvantage on attack rolls against you until the start of your next turn, as their strikes arrive where you no longer are. |

}}

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap pushes your foresight a further **6 seconds** ahead.

### Interactions & counterplay

- Electrum shows only **your own** near future, never the future of others or of objects. That wider sight belongs to atium (see the God Metals).
- **Electrum and atium cancel one another.** Your shadow splits an atium burner's view of you, and their own shifting future muddies the shadow you are reading of yourself. Between the two, neither gains a predictive edge, and the fight is settled on skill alone.
- Foresight fails if you cannot act on it: while Incapacitated or Restrained, its defensive benefits do not apply.

{{note

| | |
|---|---|
| **Base burn (1 ch/minute)** | See ~3 seconds of your own future: no surprise, advantage on initiative, immune to atium future-reading |
| **Flaring** | +3 seconds of foresight per charge: advantage on Dex saves, then a pre-emptive dodge, then disadvantage on attackers |

}}

\page

## Cadmium: Pulser

*Inside a Pulser's bubble the world slows to a crawl, and an afternoon of danger can pass outside in the space of a held breath.*

**Bloodline** Temporal Misting · **Metal** Cadmium (pure) · **Direction** External Pull · **Tempo** Minute · **Charges/gram** 30

An Allomancer burning cadmium, called a **Pulser**, creates a bubble in which time runs **slower** than the world outside./ for the shared time-bubble rules.

### Base Burn

While you burn cadmium, at a base rate of 1 charge per minute, you raise a **slowbubble**: a 15-foot-radius sphere **centered on you at the moment you raise it**. The bubble is then **fixed in space** and does not move with you. Time inside runs slowly, so that for each round experienced **inside** the bubble, **2 rounds pass outside** at base burn.

Run the bubble as its own initiative track. Each time its occupants complete one round, the outside world takes 2 rounds. Creatures and objects can move in and out freely, changing which time they experience, but **if you leave the bubble, it collapses at once**.

Holding a bubble open takes your focus, though not in the manner of a spell: **it is not broken by taking damage**. A bubble ends only when you choose to drop it, which is a free action, when you run out of metal, or when you fall unconscious.

Your burn rate is measured **from inside the bubble**, in the time you yourself experience, since you must remain within it. Because time inside runs slowly, a Pulser spends metal sparingly against the outside world's clock.

### Flaring

Each extra charge you burn, up to a number equal to your level, spends on one of the following, chosen when you raise or adjust the bubble.

- **Deepen it.** Increase the ratio by 2, so that even more time passes outside for each round within.
- **Widen it.** Increase the radius by 10 feet.

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap adds **2** to the ratio, or **20 feet** to the radius.

### Uses

- **Shelter.** Wait out a long danger in moments of your own time, letting a storm, a siege, or a pursuit pass by outside.
- **Trap.** Catch enemies inside with you; distract them to wait for backup.

### Interactions & counterplay

- The bubble is fixed where it was raised. Creatures and objects can cross its boundary freely, but you cannot, since leaving ends it.
- Cadmium and bendalloy bubbles are opposites. Their effects do not stack usefully, and a bubble within a bubble is left to the DM.
- Burning duralumin with cadmium drives the ratio to an extreme; see the core rules.

{{note

| | |
|---|---|
| **Base burn (1 ch/minute)** | 15-ft slowbubble centered on you, fixed in place; 2 rounds pass outside per round inside |
| **Flaring** | Deepen the ratio (+2) or widen the radius (+10 ft) per charge |
| **Ends when** | You drop it, leave it, run out of metal, or fall unconscious. Damage does not break it |

}}

\page

## Bendalloy: Slider

*Within a Slider's bubble, seconds stretch into minutes. A few heartbeats of the outside world are time enough to plan, to heal, and to strike a dozen times.*

**Bloodline** Temporal Misting · **Metal** Bendalloy (50% bismuth, 26% lead, 14% tin, 10% cadmium) · **Direction** External Push · **Tempo** Minute · **Charges/gram** 50

An Allomancer burning bendalloy, called a **Slider**, creates a bubble in which time runs **faster** than the world outside. It is the opposite of cadmium./ for the shared time-bubble rules.

### Base Burn

While you burn bendalloy, at a base rate of 1 charge per minute, you raise a **speedbubble**: a 15-foot-radius sphere **centered on you at the moment you raise it**. The bubble is then **fixed in space** and does not move with you. Time inside runs quickly, so that for each round that passes **outside** the bubble, its occupants experience **2 rounds** at base burn.

Run the bubble as its own initiative track. Each outside round, resolve 2 full rounds for the bubble's occupants, then advance the outside world by one round. Creatures and objects can move in and out freely, changing which time they experience, but **if you leave the bubble, it collapses at once**.

Holding a bubble open takes your focus, though not in the manner of a spell: **it is not broken by taking damage**. A bubble ends only when you choose to drop it, which is a free action, when you run out of metal, or when you fall unconscious.

Your burn rate is measured **from inside the bubble**, in the time you yourself experience, since you must remain within it. Because time inside runs fast, you spend metal faster than the outside world's clock: at a doubled bubble one outside minute costs you two minutes of burning, and a deeper bubble costs proportionally more again. Sliding hard and sliding long are both expensive.

### Flaring

Each extra charge you burn in a minute, up to a number equal to your level, spends on one of the following.

- **Deepen it.** Increase the ratio by 2, so occupants gain even more rounds for each round outside.
- **Widen it.** Increase the radius by 5 feet.

Deepening compounds against you twice over, since a deeper bubble both costs more charges each minute and burns through those minutes faster.

#### Past the cap

The flare cap is where an ordinary Allomancer stops. A duralumin detonation, or savancy, takes you past it, and past it the scaling continues at a flat rate: **for every 2 charges beyond your cap**, add the following. There are no further tiers, so the whole of a burst is one multiplication.

Each 2 charges past the cap adds **2** to the ratio, or **10 feet** to the radius.

### Uses

- **Act many times.** You and your allies inside gain extra rounds against a slower outside world, to attack, heal, or prepare.
- **Race the clock.** Cover in moments a task that would take far longer.

### Interactions & counterplay

- The bubble is fixed where it was raised. Creatures and objects can cross its boundary freely, but you cannot, since leaving ends it.
- Burning duralumin with bendalloy detonates your whole reserve into a single instant of extreme compression, so that a long span inside passes in a blink outside. See the core rules.
- **Emotional Allomancy inside your own bubble rivals a duralumin burst.** Because your burn is measured in *your* fast time, a Rioter or Soother working from inside their own speedbubble pours out charges far faster than the outside clock: at a 16-to-1 bubble, even one emotional charge per (inside) round lands as sixteen charges in a single outside round, enough to sweep or overwhelm a crowd. Unlike firing across a bubble's edge, a pulse aimed from *within* your own bubble is not disrupted, so it can still be targeted normally.
- Cadmium and bendalloy bubbles are opposites and do not stack usefully.

{{note

| | |
|---|---|
| **Base burn (1 ch/minute)** | 15-ft speedbubble centered on you, fixed in place; occupants gain 2 rounds per outside round |
| **Flaring** | Deepen the ratio (+2) or widen the radius (+5 ft) per charge |
| **Ends when** | You drop it, leave it, run out of metal, or fall unconscious. Damage does not break it |

}}

\page

## God Metals of Allomancy

*Not a quadrant. A category, and a campaign event.*

The God Metals are formed from the power of a Shard rather than mined from the ground. They are not bloodlines chosen at character creation; they are rare materials a DM places, and each one does something no ordinary metal can. A bead of atium is a treasure. A bead of lerasium rewrites a character sheet. Expect the world to react to anyone known to hold either.

{{imgph,style=min-height:17em
<!--h:15-->
**[ART: godmetals-atium]** *A single bead of atium on dark cloth, catching no light it should.*

**COLUMN** not supplied | ratio 1.33:1
}}
::::

## Other Metals

The sixteen metals of the four quadrants are the Allomancy an ordinary Metalborn can be born to. Beyond them lie the **God Metals**, formed directly from a Shard, and their alloys. These are **not bloodlines you choose at character creation.** They are rare, campaign-shaping materials the DM places in the world.

See the God Metals for the lore and the core rules for the shared burn rules.

### How Other Metals differ

- **Rarely chosen at creation.** A person *can* be born an atium Misting, and a few are, but atium is scarce enough that almost none of them ever find out. Access is usually a matter of story rather than birth: a found cache, a patron's gift, a spike, a bead pressed into your hand at the worst possible moment.
- **Scarce by design.** Atium and malatium are priced as treasure, not equipment. Lerasium is not purchasable at any price.
- **A Mistborn burns them innately**, though at reduced efficiency until they learn them properly; see the core rules.

### The metals

- atium, the god metal of **Ruin**. Shows you the immediate future of everyone around you. The deadliest combat metal in the setting.
- malatium, atium alloyed with gold, called the **Eleventh Metal**. Shows you another person's alternate past.
- lerasium, the god metal of **Preservation**. Burning it makes you a Mistborn. A reward at the level of a legendary artifact.

### Setting material, not player options

Two further God Metals exist on Scadrial and are **not playable**. They are here so a DM can use them.

**Harmonium**, called *Ettmetal* in the south, is the god metal of Harmony. It burns with a pure whiteness and **explodes violently on contact with water or any liquid**, which makes ingesting it for Allomancy nearly impossible. The Southern Scadrians use it to power machinery. Its Allomantic and Feruchemical properties remain unknown.

**Trellium**, also called *Bavadinium*, is the god metal of Autonomy: silvery with a red cast and dark red spots like rust. Its Allomantic and Feruchemical properties are unknown. Hemalurgically it can grant Allomantic or Feruchemical powers to a Kandra, and it is used to make Hemalurgic constructs. A creature bearing a single trellium spike is hidden from Harmony.

### DM guidance

Treat these metals as plot, not as loadout. A vial of atium should change what a session is about. When you hand out lerasium, you are handing out a new character.

\page

## Atium: Seer

*The world fills with ghosts. Every creature drags a shadow of itself a heartbeat ahead, and a Seer needs only to strike where the shadow is going to be.*

**Metal** Atium (god metal of Ruin) · **Tempo** Round · **Charges/gram** 10 · **Availability** DM-gated treasure

Burning atium shows you the **immediate future of everyone around you**. It is the deadliest combat metal on Scadrial and the reason an empire's economy was built on a single mine. This is not a bloodline taken at character creation; see other metals.

### Base Burn

While you burn atium, at a base rate of 1 charge per round, every creature you can see within **120 feet** is led by an **atium shadow** showing what it is about to do, roughly **3 seconds** ahead. Your mind is heightened to take it in and act upon it.

- Attack rolls against you have **disadvantage**.
- You have **advantage** on attack rolls, on Dexterity saving throws, and on ability checks made to react to a creature you can see.
- You cannot be **surprised**, and you know a creature's intended action a moment before it takes it.

**The limits of foresight.** Atium does not falter against numbers. A Seer reads a score of enemies as easily as one, and has cut through whole ranks of koloss untouched. What foresight cannot do is move your body for you. Where you physically cannot get out of the way, the knowledge is worthless: while you are Grappled, Restrained, or Incapacitated, or while you are so hemmed in that there is nowhere left to step, attacks against you are made normally.

### Flaring

Each extra charge you burn in a round, up to a number equal to your level, pushes the shadows further ahead, about **3 seconds per charge**. The range remains 120 feet; what grows is how far into the future you see. At a few seconds you read the next blow, and at a dozen you read the whole exchange before it begins.

{{tableGroup

### Refined atium

Raw beads are what most Seers ever see. **Refined** atium does not add to its foresight, it multiplies it: each charge **doubles** the time you see ahead rather than adding to it.

| Charges | Raw atium | Refined atium |
|---|---|---|
| 1 | 3 sec | 3 sec |
| 2 | 6 sec | 6 sec |
| 3 | 9 sec | 12 sec |
| 4 | 12 sec | 24 sec |
| 5 | 15 sec | 48 sec |
| 8 | 24 sec | about 6 minutes |
| 10 | 30 sec | about 25 minutes |

}}

Refined atium also enhances the mind to hold and process what it shows, and at the deepest burns it opens sight into the **Spiritual Realm**. It is the only form usable in Hemalurgy, where it acts as a wild card able to steal any power. Treat refined atium as a story artifact.

### Interactions & counterplay

- **Atium and electrum cancel one another.** An Oracle's split shadow cannot be read, and their own foresight is muddied by yours in turn. Neither of you gains an edge.
- **Two atium burners cancel** each other the same way, and the fight comes down to skill and reserves.
- Atium burns at round tempo and holds only 10 charges to the gram. A single gram is one minute of foresight. Reserves are measured in seconds, not fights.

{{note

| | |
|---|---|
| **Base burn (1 ch/round)** | See 3 seconds ahead for every creature within 120 ft; disadvantage on attacks against you, advantage on yours, no surprise |
| **Flaring** | +3 seconds of foresight per charge; range stays 120 ft |
| **Limit** | Foresight is useless where you physically cannot evade |
| **Refined** | Foresight doubles per charge instead of adding; opens Spiritual Realm sight |
| **Cancelled by** | Electrum, and other atium |

}}

\page

## Malatium: the Eleventh Metal

*A stranger stands beside your enemy wearing their face, living the life they did not choose. Watch them long enough and you will learn who your enemy truly is.*

**Metal** Malatium (atium alloyed with gold) · **Tempo** Round · **Charges/gram** 10 · **Availability** DM-gated treasure

Malatium is atium turned outward through gold. Where gold shows you **your own** alternate past, malatium shows you **another person's**. Legend named it the **Eleventh Metal** and held that it could undo a tyrant. The legend was not wrong, though what the metal offers is knowledge rather than a weapon. This is not a bloodline taken at character creation; see other metals.
### Base Burn

While you burn malatium, at a base rate of 1 charge per round, choose one creature you can see. A translucent shadow of that creature appears beside it, living out a life shaped by choices it did not make.

Reading the shadow reveals something true about the target that they have hidden or that even they have forgotten: their origin, their true name or identity, a pivotal choice in their past, or the shape of the person they might have been. If you are able to touch the shadow, you will be granted a moment as them. The DM decides what surfaces, and one meaningful truth per subject is the usual measure.

This is an investigative and dramatic tool rather than a combat one. It reveals **the past**, never the future.

### Flaring

Each extra charge you burn in a round, up to a number equal to your level, holds the vision longer and draws it clearer, letting you follow the alternate life further from its branching point and pull more detail from it.

### Interactions & counterplay

- Malatium reads a life, not a mind. It cannot tell you a creature's current plans, and it grants no combat benefit.
- A creature whose identity has been rewritten by outside power, such as a Forgery, shows a shadow shaped by the altered self rather than the original.
- Like atium, malatium is vanishingly rare and priced as treasure.

{{note

| | |
|---|---|
| **Base burn (1 ch/round)** | See one visible creature's alternate past; learn a hidden truth about them |
| **Flaring** | Longer, clearer vision and more detail per charge |
| **Note** | Investigative and narrative; no combat effect, and it never shows the future |

}}

\page

## Lerasium

*Nine beads made nine houses into legends, and every Allomancer who has lived since is descended from that gift.*

**Metal** Lerasium (god metal of Preservation) · **Tempo** Instant · **Availability** Legendary reward only, never purchasable

Lerasium is condensed Preservation. Burning it does not grant a power for a time; it **remakes the person who swallows it**. This is not a bloodline, and it is not equipment. Treat a bead of lerasium as a legendary artifact and a story event. See other metals.

### Burning a bead

Burning a bead of lerasium is instantaneous and permanent, and a single bead is all that will ever matter. Choose one of the following.

**Become Mistborn.** You permanently gain the ability to burn all sixteen Allomantic metals, becoming a **Mistborn**. If you had a Misting bloodline, it is subsumed into the whole. Training is still required to use unfamiliar metals well; an untrained Mistborn burns most metals at reduced efficiency until they learn them, as described in the core rules.

**Amplify what you are.** If you already have a Misting bloodline and keep it, that single power is permanently strengthened beyond the reach of a true Mistborn. Your **flare cap** for that metal increases by an amount the DM sets, and your charges count as doubled for magnitude and for the surge threshold, as a savant's do, without the savant's dependency.

The size of the bead is proportional to the power granted. Larger beads are the stuff of legend rather than treasure.

### Bloodline and inheritance

Lerasium's gift is **heritable**. The Allomancy of the Final Empire descended from nine beads over a thousand years, diluting into Mistings as generations passed. A character remade by lerasium may found a line, which is a campaign consequence worth more than any combat benefit.

### Interactions & counterplay

- Burning enough lerasium to become a **savant** of it would instead cause **Ascension**, making the burner the Vessel of Preservation.
- Used in **Hemalurgy**, a lerasium spike steals all of a victim's abilities at once.
- Its Feruchemical properties are unknown.

### DM guidance

Handing out lerasium rewrites a character sheet and shifts the balance of a campaign. Give it when the story has earned it, and expect the world to react: in the Final Empire, being known to hold a bead was reason enough to be hunted.

{{note

| | |
|---|---|
| **Burning a bead** | Permanent: become a Mistborn, or permanently amplify one existing Misting power |
| **Availability** | Legendary reward only, never for sale |
| **Danger** | Enough to reach savanthood causes Ascension |

}}

\page

## Savants

*Burn a metal long enough and hard enough and it stops being a tool you pick up. It becomes part of you, always there, and its absence becomes a wound. That is a savant: not merely skilled, but fused, past the limit an ordinary Allomancer can safely reach, and unable to go without.*

A **savant** is an Allomancer whose soul has grown into a single metal through relentless use. Spook burning tin until the world screamed at him, the assassins of legend who lived on pewter: these are savants. Savancy is the only way to burn a metal **past its normal flare cap**, and it always comes with a price. Individual Misting pages call out what a savant of *their* metal can do; the Mistborn gains savancy through class features as well as through use.

### What a savant gains

Being a savant of a metal grants three things, together, for that one metal.

- **A doubled cap.** Your flare cap for that metal is **twice your level** rather than equal to it. This is the heart of savancy, and it is why a savant reaches feats an ordinary Allomancer cannot. It is not the removal of the cap: only a duralumin detonation does that, spending everything you hold in one instant.
- **Doubled efficiency.** Your **spent charges count as doubled** toward magnitude and toward the surge threshold, and **each charge lasts twice as long**. A savant reaches the surge tier at about **10 real charges** rather than 20, and their reserves stretch twice as far.
- **The Dependency (always).** Your body has come to rely on the burn. This price is never waived, not by class, not by ascension, not by any Mistborn's stronger soul. See below.

The doubled cap and the doubled efficiency work together: the cap lets you *spend* the charges, the doubling makes them *land* harder. Without savancy, an ordinary Allomancer only reaches that tier near 20th level or through a one-time Duralumin detonation.

### The Dependency

A savant's power is inseparable from its cost. **Whenever you are a savant of a metal and you are not burning it**, whether your reserve has run dry or you have simply stopped, you fall into **withdrawal** until you burn that metal again.

- You have **disadvantage on ability checks and saving throws tied to that metal's gift**, at the DM's read of what the metal gave you. A **tin** savant loses their edge on Perception and Dexterity; a **pewter** savant on Strength and Constitution; a **bronze** savant can no longer feel Allomancy at all.
- Metals that **sharpen the senses dull them below normal** in withdrawal. A tin savant cut off from tin is briefly half-blind and deaf to the ordinary world, their unamplified senses feeling muffled and wrong, until they burn again.
- The withdrawal **lands the moment you stop** and **lifts the moment you resume**. It is not exhaustion you can sleep off; it is a hunger only the metal answers.

**Severity varies by metal.** The Dependency is not equally harsh for every metal. **Tin** and **pewter** are the cruelest: a tin savant's raw senses are painfully wrong without the burn, and a pewter savant, having felt neither pain nor exhaustion, has often ignored the wounds that then kill them. **Copper** is famously *mild* (a Smoker savant is far less troubled by going without than most), and **bronze** so mild that many Seekers become savants without ever noticing. Use the tiers below unless a metal's own page says otherwise:

- **Severe** (tin, pewter): disadvantage as above, *and* while in withdrawal you also have disadvantage on the associated saving throws; senses drop below a normal person's.
- **Moderate** (most metals): disadvantage on that metal's tied checks and saves until you resume.
- **Mild** (copper, bronze): disadvantage on that metal's tied checks only; no worse. The savant scarcely feels tethered.

A savant is therefore never truly free of the metals they have fused with. The greatest Allomancers in the histories were also, quietly, the most tethered, though some metals bind more gently than others.

\page
### Becoming a savant

There are two roads to savancy.

#### Route 1: long use (organic)

Available to **any** Allomancer, Misting or Mistborn. You become a savant of a metal once you have **burned about 5 kilograms (5,000 grams) of it over your lifetime**.

- Track a metal's progress as **total grams burned**, across your whole career. This single unit works for *every* metal, including the instant-tempo enhancement metals that are never "lit for hours." The DM tracks it loosely; the exact gram is never the point.
- **Real time-to-savant varies by metal, and that is intended.** Grams accrue at wildly different rates depending on a metal's tempo and how you use it:
 - A metal you **leave lit** through your waking hours reaches 5 kg in roughly **a year** (tin), or **half a year** for a cheaper-burning one (bronze, copper). This is why Seekers become bronze savants almost by accident.
 - A metal you burn only in **bursts** (pewter in a fight, steel for a jump) accrues far more slowly in practice, so its savants are rare. Most Thugs die on the battlefield long before they burn five kilograms of pewter.
 - An **instant enhancement metal** (aluminum, chromium, duralumin, nicrosil) accrues a gram only across thousands of individual burns; its savants are the rarest of all, barely attested, exactly as the histories suggest.
- **Flaring accelerates it.** The histories say savants are made by long, sustained *flaring*, and the gram meter captures that on its own: flaring spends charges several times faster than base burn, so it eats through metal faster. An Allomancer who habitually flares reaches five kilograms far sooner than one who merely simmers.
- A Mistborn may take this road only for a metal they have **mastered** (an unmastered metal is burned too poorly to fuse with).

#### Route 2: class features

The Mistborn gains savancy directly, by fiat, through class features, skipping the year of use:

- **14th-level Quadrant Resonance** makes you a savant of your **starting quadrant's four metals**.
- **Allomantic Savant (17th)** and **Deepening Mastery (18th)** each make you a savant of chosen metals beyond that.
- **Mistborn Ascendant (20th)** makes you a savant of **every** metal you burn.

Every one of these carries **the Dependency** all the same. A 20th-level Mistborn is a savant of all sixteen metals and, correspondingly, is at risk of withdrawal from any metal they were leaning on the moment they are cut off from it, the classic vulnerability of the greatest Allomancers.

### Interactions

- **Aluminum and chromium** still wipe a savant's reserve in an instant, which for a savant does not merely disarm them but plunges them straight into withdrawal. Savants are especially afraid of Leechers.
- **Duralumin** lets *any* Allomancer touch the surge tier once by detonating their reserve; a savant does not need it to get there, and can reach that tier repeatedly and at will (at the cost of the charges).
- **Compounding** (Compounding) and savancy are independent. A Feruchemical-fed reserve makes it *easier* to burn a metal habitually enough to become a savant, and easier to sustain the burn that keeps withdrawal at bay.

\page
{{tableGroup

### Savant effects by metal

Every savant gains the shared package (a doubled cap, doubled efficiency, the Dependency). On top of that, long fusion with a particular metal grants signature effects drawn from the histories. Each metal's own page carries the full rules; this is the summary.

| Metal | What savanthood adds | Dependency |
|---|---|---|
| **Tin** | Ordinary light becomes blinding (a savant goes veiled and gloved by day), but hearing and touch grow so acute they compensate for lost sight, letting the savant fight half-blind and *anticipate* attacks almost as a Seer reads atium. | Severe (senses wrong without it; oddly, a dulled sense of pain) |
| **Pewter** | Wounds close faster (never as fast as a tapped goldmind), and pain and fatigue all but vanish. | Severe, and *deadly*: feeling no wound, a savant may fight on past a fatal one |
| **Copper** | The coppercloud grows stronger and harder to pierce. | **Mild** (Smokers bear it easily) |
| **Bronze** | Range expands; the savant can pierce copperclouds (contested by their strength against the cloud), and can tell ordinary Allomancy from **Compounding**. | **Mild** (many Seekers savant unknowingly) |
| **Cadmium** | Slows time more deeply; the bubble may be **anchored to the savant and move with them**, and its size and the degree of slowing become adjustable. Objects crossing the boundary suffer the usual energy-transfer complications. | Moderate |
| **Bendalloy** | Quickens time more deeply; likewise a **moving bubble** anchored to the savant, with adjustable size and degree. | Moderate |
| **Aluminum** | Beyond purging one's own metals, the savant can **cleanse their spirit of unwanted Investiture**, ending even powerful magical or Invested effects on themselves. | Moderate |
| **Others** | Not clearly attested in the histories; the DM sets the signature effect in keeping with the metal, using the shared package as the floor. | Per tier above |

}}

\page
## Savants of particular metals

Four metals have savant effects specific enough to state outright. The rest follow the shared package above.

### Tin

A tin savant (about 5 kg of tin burned over a lifetime, or a Mistborn's class feature) has fused with the metal. Beyond the shared savant package (a doubled cap, doubled efficiency, the Dependency), the fusion reshapes their senses:

- **Ordinary light blinds them.** A tin savant burning tin treats normal daylight as the *Sensory Overload* trigger against sight, which is why the famous ones go **veiled and gloved by day**. In exchange, their hearing and touch grow so acute that they can fight and move **half-blind without penalty**, and can **anticipate attacks** almost as a Seer reads atium: while burning tin, attackers you can hear and feel do not gain advantage from being unseen, and the DM may grant you a read on an incoming blow.
- **The Dependency is severe.** Cut off from tin, the savant's raw senses feel muffled and wrong (disadvantage on Perception checks and Dexterity saves until they burn again); oddly, their untethered nerves also **dull their sense of pain**.

### Pewter

A pewter savant (about 5 kg of pewter burned, or a Mistborn's class feature), beyond the shared savant package (a doubled cap, doubled efficiency, the Dependency), heals faster than a natural body, though never as fast as someone tapping a goldmind: while burning pewter you regain a small amount of hit points at the start of each of your turns, at the DM's rate. Pewter savants are rare for a grim reason. Feeling neither pain nor exhaustion to any real degree, a savant can **ignore wounds that later prove fatal**, and many Thugs die on the battlefield, still fighting, long before they ever burn five kilograms of pewter. The savant's Crash, when it lands, is correspondingly worse.

### Cadmium

A cadmium savant (5 kg burned, or a Mistborn's class feature), beyond the shared savant package (a doubled cap, doubled efficiency, the Dependency), transcends the fixed bubble:

- Your slowness bubble may be **anchored to you and move with you**, so you can walk while wrapped in slowed time rather than being pinned to a sphere on the ground. Creatures and objects crossing the moving boundary suffer the usual energy-transfer complications as time re-seats them.
- You may **slow time more deeply than an ordinary Slider**, and freely **adjust the bubble's size and the degree of its slowing** on the fly, within your charges.

### Bendalloy

A bendalloy savant (5 kg burned, or a Mistborn's class feature) transcends the fixed bubble. In addition to the shared savant package (a doubled cap, doubled efficiency, the Dependency):

- Your bubble may be **anchored to you and move with you**, so you carry your quickened time as you walk rather than being trapped in a sphere on the ground. Objects and creatures crossing the moving boundary suffer the usual energy-transfer complications as time re-seats them.
- You may freely **adjust its size and the degree of its speed-up** on the fly, within your charges, rather than setting them only as you raise it.

### Feruchemical savants (through Compounding)

Savanthood is not only Allomantic, but it is **much harder** to reach Feruchemically. Feruchemy draws on no power from outside you, so nothing accumulates to etch the soul; in practice the only road is **Compounding**, which does draw on an outside source. A Feruchemist who Compounds a single metal relentlessly fuses with their *Feruchemy* the way heavy burning fuses an Allomancer with a metal.

A Feruchemical savant of a metal:

- **Can use that Feruchemy without a metalmind**, storing and tapping the attribute directly, the art's most coveted mastery.
- **Deepens the Compounded effect** (a gold Compounder-savant outlasts even an ordinary gold Compounder, surviving what should kill them again and again).
- **Carries its own dependency:** the body that never stops mending cannot safely stop. Miles Dagouter is the warning.

\page
## Ferring Bloodlines

A **Ferring** is a person who can Feruchemically **store one attribute** in metal and **tap** it back later. A Ferring power is a **bloodline**, chosen at character creation and independent of your species and class, exactly as a Misting power is.

Feruchemy is the art of balance. You take nothing from outside yourself: you set a portion of what you are into metal now, going without it, so that you may draw it back later in a rush./; lore from Feruchemy.

### Gaining the bloodline

- Chosen at **character creation**. Unlike Allomancy, Feruchemy needs no Snapping; it is available as soon as the trait is present.
- Your **bloodline level equals your character level**, whatever your class.
- Your **Feruchemical ability is Constitution**.

### Metalminds

A piece of your metal used for storage is a **metalmind**: a ring, a bracer, a stud, a spike, or a bead.

- A metalmind must be **in contact with you** to store or tap. It may be **worn** against the skin, **embedded** in it as a piercing or a spike, or **swallowed** and carried inside you. Terris bracers that pierce the flesh are a common choice for those who mean never to be parted from their store.
- **Internal metalminds matter for Compounding.** A Twinborn can only Allomantically burn a metalmind that is inside their body, so a Compounder relies on swallowed beads or embedded spikes. See the core rules.
- A worn metalmind can be taken from you. An embedded or swallowed one cannot, short of surgery.
- Metalminds are **keyed to your Identity**. Only you can tap what you filled, unless the mind is **unsealed**. A mind is keyed the moment it is filled and **cannot be unsealed afterward**; an unsealed mind must be filled that way from its very first charge, by someone storing their own Identity as they fill it. See Trueself and the Feruchemist class.
- A stored charge **does not decay**. It waits as long as you leave it.
- A **heavily charged metalmind resists damage and destruction** far better than an empty one. Deep Investiture toughens the metal itself, so a full ring is harder to melt, bend, or break than a bare one of the same make.
- **Capacity is 10 unit-minutes per gram**, where one unit-minute is 100% of the attribute held for one minute.
- Melting a metalmind preserves its charge; alloying it away destroys the charge; splitting it divides the charge.

# The Feruchemical Metals

{{wide
<!--h:44-->
![chart-feruchemy](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/chart-feruchemy.svg?v=16b55c8d){width:100%}
}}

\page
### Storing and tapping

Both are **free actions** and take effect instantly. Stop, and you return to normal at once with no lingering penalty. You must be **conscious** to store or tap, with one exception: wakefulness may be stored while you sleep.

**Intensity and time.** You choose how hard to store and how hard to tap.

- **Storing** at intensity `s` means giving up that fraction of the attribute for as long as you fill. Storing 20% of your strength for an hour banks 0.2 × 60 = **12 unit-minutes**.
- **Tapping** at intensity `t` means gaining that fraction back on top of your normal self. Tapping at 1.0 means +100%, or double.

**Your rate and your depth.** Two numbers govern a Ferring, and both rise with level.

- **Your rate** is the intensity you can draw without strain: **50% per level**, and it keeps climbing to the end.
- **Your depth** is the hardest you can store: **10% per level**, reaching the full **100% at 10th level**. It rises no further, because you cannot give up more of an attribute than you have.

| Level | 1 | 2 | 3 | 4 | 5 | 10 | 15 | 20 |
|---|---|---|---|---|---|---|---|---|
| **Rate** (free draw) | +50% | +100% | +150% | +200% | +250% | +500% | +750% | +1,000% |
| **Depth** (max store) | 10% | 20% | 30% | 40% | 50% | 100% | 100% | 100% |

After 10th level the two part ways, and this is the shape of a Ferring's career. You can bank no deeper than you already could, but you grow ever better at spending what you banked.

{{tableGroup

#### What the percentage multiplies

A percentage means nothing until you say what it is a percentage **of**. Every metal names one concrete, measurable **attribute**, and tapping at +X% multiplies that attribute by 1 + X/100.

| Metal | The attribute |
|---|---|
| Iron | your body weight |
| Steel | your movement rate |
| Pewter | your force output, measured as carrying capacity |
| Tin | your sensory acuity, measured as the distance at which a given detail is perceptible |
| Zinc | your rate of thought, measured as time taken to work something out |
| Brass | your body heat |
| Bronze | your alert waking time |
| Copper | **nothing.** See below |

}}

Each metal's page then translates that quantity into play. A Ferring drawing many multiples of their rate can reach several thousand percent for a few seconds, so every attribute needs to know its own ceiling and its own way of hurting you.

**Some metals bend the frame.** Not every attribute is a smooth intensity you multiply. Three shapes recur:

- **Intensity attributes** (weight, speed, strength, senses, mental speed, determination) work exactly as above: tap at +X% to multiply them, bounded by rate, depth, and compression.
- **Reserve attributes** (breath, nutrition) are consumables, banked in their own natural units, minutes of air, days of food, and spent later. There is no intensity and no compression; you fill a pool and draw it down. See cadmium and bendalloy.
- **Concrete-quantity attributes** measure a real physical thing and set the percentage aside for its own unit:
 - **Copper** stores discrete **memories**. Counted in memories; rate, depth, and compression do not apply. See Copper.
 - **Brass** stores **energy**, drawn from outside the body as readily as within. Counted in **kilojoules**, no percent-of-self ceiling, rate and depth replaced by a level-gated **throughput**; compression applies and runs harsh. See Brass.
 - **Gold** stores **health**. Counted in **hit points**, banked while sick and spent to heal. Its free heal rate is set by Constitution and proficiency, its harshness lives in the sickness of storing and the flat 2-for-1 of cheating death, and ordinary healing runs on the standard curve. See Gold.

{{tableGroup

#### Compression

Drawing at your own rate costs you nothing. Pushing past it does, and the price climbs quickly. Divide the intensity you want by your rate to get the **multiple**, then read your recovery.

| Multiple of your rate | 1× | 2× | 3× | 4× | 5× | 6× | 8× | 10× |
|---|---|---|---|---|---|---|---|---|
| **Recovery** | 1.00 | 0.80 | 0.64 | 0.51 | 0.41 | 0.33 | 0.21 | 0.13 |

}}

```
tap duration = stored units × recovery ÷ tap intensity
```

Recovery never exceeds 1.00. Feruchemy grants no profit, only a change in timing.

*Example.* A 3rd-level Ferring has a rate of +150%, and their 5-gram ring holds 50 unit-minutes.

- Drawing at **+150%**, one multiple of their rate, loses nothing: `50 × 1.00 ÷ 1.5 =` about **33 minutes**.
- Drawing at **+300%**, two multiples, recovers 0.80: `50 × 0.80 ÷ 3.0 =` about **13 minutes**.
- Drawing at **+450%**, three multiples, recovers 0.64: about **7 minutes**.

\page

There is no hard ceiling on how hard you may draw. The losses are the ceiling. Past a few multiples of your rate you are spending a whole ring to buy seconds, which is sometimes exactly what a Ferring wants.

**Nothing about a metalmind is tracked except how much is in it.** How it was filled, over how long, and at what intensity, makes no difference to what you get out. Compression is a fact about *you*, not about the ring.

### Starting equipment

A Ferring begins play with a **ring** of their metal weighing **1d8 grams**, and the knowledge of how to use it.

{{imageMaskCorner21,--offsetX:0%,--offsetY:-30%,--rotation:0
  ![The Feruchemical metals, by the Ferring starting equipment](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/ferrings-feruchemical-metals.png?v=12c46146){height:100%}
}}

\page
# Quadrant Disciplines

### Physical

*Four metals for the body, and the plainest bargain in Feruchemy.*

The Physical quadrant stores what a body is and does: weight into iron, speed into steel, senses into tin, strength into pewter. Nothing here is subtle. You spend an afternoon slow, dull, weak or oddly light, and you get that afternoon back concentrated into the thirty seconds you needed it. Because the trade is so legible, this is the quadrant that rewards planning: a Skimmer who filled their ironmind yesterday can walk on a rope bridge that will not hold anyone else, and a Brute who did not fill anything is simply a person.

::::

## Iron: Skimmer

*A Skimmer crosses rotten floorboards without a creak, then plants themselves in a doorway and becomes something no charge can move.*

**Bloodline** Physical Ferring · **Metal** Iron (pure) · **Attribute** Physical weight · **Capacity** 10 unit-minutes per gram

A **Skimmer** stores their own **weight** in an ironmind. See the Ferring Bloodlines for the shared rules.

### Storing

While you fill an ironmind, you grow lighter by the fraction you are storing. Your body is unchanged in size and strength; it simply weighs less.

- You are correspondingly easier to move, throw, and knock about. Forced movement against you travels further, and you have disadvantage on saves to resist being shoved or pushed.
- You fall more slowly against the air, reducing falling damage in proportion to how light you have made yourself.
- You tread more lightly, and at some point that becomes useful. What a given lightness makes possible is a matter of what you now weigh:

| Weight stored | What becomes possible |
|---|---|
| −25% | Nothing mechanical. You are simply light on your feet. |
| −50% | You can cross what would hold half your weight: weak boards, thin ice, a tired rope bridge. Advantage on Dexterity (Stealth) checks that depend on your footfalls. |
| −90% | Snow crust, mud, and narrow ledges hold you. Pressure plates and weight-triggered traps do not fire. |
| −99% | You drift more than you walk. A stiff wind becomes a genuine problem, and a shove sends you a long way. |

{{tableGroup

### Tapping

While you tap an ironmind, you grow heavier by the intensity you draw, and you are granted the strength to carry that weight without being crushed by it. Your density rises with your weight, though your size does not.

| Tap intensity | Effect |
|---|---|
| +100% (double) | Advantage on saves and checks to resist being moved, shoved, or knocked prone. You cannot be pushed by Steelpushing beyond half the normal distance. |
| +200% to +300% | You are immovable by ordinary force: forced movement against you fails unless the source is magical or itself Feruchemically strengthened. Your falling and charging attacks add momentum, dealing an extra 1d6 damage per 100% stored above your base. |
| +400% or more | Your weight becomes a hazard to the ground beneath you. You may break through floors, sink in soft earth, and swim not at all. Ordinary furniture, boats, and ropes fail under you. |

}}

### Limits

Weight is not armor. Your increased density does **not** protect you from being pierced or cut, and a heavier body is still a body. Momentum is conserved: a heavy Skimmer who is already moving is very hard to stop, and just as hard to turn. Tapping enough weight on unsuitable ground means going through it.

### Interactions

- A Skimmer paired with a Coinshot or Lurcher is the classic pairing. Store weight to be launched further on a Push, then tap weight to land like a dropped anvil, or to anchor yourself so that the Push moves the target instead of you. See the **Force Tables**, reading your altered weight.
- Weight changes what the force tables do to you. A Skimmer is the one creature whose row in those tables moves during a fight.

{{note

| | |
|---|---|
| **Attribute** | Physical weight |
| **Storing** | Lighter: easier to move, softer footfalls, gentler falls |
| **Tapping** | Heavier: hard to move, added momentum, eventually a hazard to the floor |
| **Limit** | Density does not stop a blade, and momentum cuts both ways |

}}

\page

## Steel: Steelrunner

*A Steelrunner spends the morning moving as though through cold honey, and buys with it ten seconds in which no one else in the room can react at all.*

**Bloodline** Physical Ferring · **Metal** Steel (98% iron, 2% carbon) · **Attribute** Physical speed · **Capacity** 10 unit-minutes per gram

A **Steelrunner** stores their own **physical speed** in a steelmind. Sazed counted steelminds among the hardest of all to fill, since the storing is so wearying to live through. See the Ferring Bloodlines for the shared rules.

### Storing

While you fill a steelmind, every movement comes slower, as though you were wading through molasses. Reduce your speed by the fraction you are storing.

- At light storing you are merely sluggish. At heavy storing you have disadvantage on initiative, on Dexterity checks, and on Dexterity saving throws.
- Fine work is not impossible, only slow. Storing speed does not dull your mind or weaken your body.

{{tableGroup

### Tapping

While you tap a steelmind, you move faster than a body has any right to. **Multiply your speed by 1 plus the intensity you draw.**

Your perception and reflexes quicken along with your body, enough to navigate at that pace. You see the doorway coming and take it, and the world does not blur past unread. This is **not** quickened thought. You do not reason faster, plan faster, or make more decisions, which is the work of Feruchemical zinc.

| Tap intensity | Effect |
|---|---|
| +100% (double) | Your speed doubles, and you have advantage on initiative and on Dexterity saving throws. |
| +200% to +300% | Your speed triples or quadruples. You can take the Dash or Disengage action as a bonus action. Opportunity attacks against you are made with disadvantage. |
| +400% or more | You gain **one additional action** on each of your turns, spent only to Attack, Dash, Disengage, Hide, or Use an Object. To onlookers you are a blur crossing the room between heartbeats. |

}}

**The action ceiling.** One extra action is all steel will ever give you, no matter how hard you draw. Everything past +400% becomes raw velocity, not more decisions, because deciding is the mind's work and steel only carries the body.

{{tableGroup

### Limits

Speed does not exempt you from the world, though it takes a great deal of speed before the world objects. A base walking speed of 30 feet per round is only about 3.4 miles per hour, so the early tiers are unremarkable.

| Tap intensity | Speed | About | Effect |
|---|---|---|---|
| up to +900% | up to 300 ft/round | 35 mph | No penalty. Fast, but nothing a body cannot take. |
| +1,900% | 600 ft/round | 70 mph | Unprotected, the wind blinds and deafens you: disadvantage on Perception checks. **Goggles, a helmet, or a wrapped face negate this.** |
| +4,900% | 1,500 ft/round | 170 mph | The air is a wall. You take **1d6 bludgeoning damage** at the end of each turn unless fully protected, and you cannot stop or turn safely. |
| +9,900% or more | 3,000 ft/round | 340 mph | Heat and pressure tear at you regardless of gear. Sustained running at this speed is suicide. |

}}

**Collisions.** At these speeds, running into something is not a stumble. Resolve it with the impact damage table among the **Force Tables**, using your mass and your actual speed. A Steelrunner meeting a wall at 250 feet per second is doing the same physics as a body hurled by a Coinshot.

Because compression punishes hard draws, the highest tiers last seconds, not minutes. A Steelrunner sprints; they do not cruise.

### Interactions

- A Steelrunner's speed is movement and reaction, not thought. For quickened thinking, that is Feruchemical zinc.

{{note

| | |
|---|---|
| **Attribute** | Physical speed |
| **Storing** | Sluggish; reduced speed, eventually disadvantage on Dex and initiative |
| **Tapping** | Speed × (1 + intensity); perception keeps pace; bonus-action Dash, then one extra action |
| **Ceiling** | One extra action, ever. Beyond that, speed only, since deciding is zinc's work |
| **Limit** | Nothing until ~35 mph; wind at 70 mph (gear negates); real damage from 170 mph |

}}

\page

## Tin: Windwhisperer

*A Windwhisperer wears a half-dozen rings and chooses, each morning, what they will be able to do that day: read a page across a courtyard, hear a whisper through a wall, or feel nothing at all.*

**Bloodline** Physical Ferring · **Metal** Tin (pure) · **Attribute** Senses, one per metalmind · **Capacity** 10 unit-minutes per gram

A **Windwhisperer** stores the **sensitivity of their senses** in tinminds. See the Ferring Bloodlines for the shared rules.

### One sense to a metalmind

Each sense must be stored in its **own tinmind**. A ring holding sight holds nothing else. This is what makes Windwhisperers so recognizable: they wear many rings and know each by touch.

You are not limited to the traditional five. Any sense you actually possess can be stored, including **the ability to feel pain**, your sense of balance, or other such senses. A creature with senses beyond the human range can store those too.

### Storing

While you fill a tinmind, the sense you are storing dulls in proportion.

- **Sight** fades toward nearsightedness and then blindness. **Hearing** dims toward deafness. **Touch** goes numb.
- **Pain** is the prize. A Windwhisperer storing pain feels nothing from a wound, which is as dangerous as it is useful, since you will not notice what is killing you. While storing pain heavily, you automatically fail checks to notice injury and you may keep acting past the point of good sense, at the DM's discretion.
- You may store several senses at once in several metalminds, and dull yourself nearly to nothing.

{{tableGroup

### Tapping

While you tap a tinmind, that one sense sharpens beyond human range. Tapping only strengthens what a sense can already do.

**The attribute is distance.** Tapping at +X% multiplies **the range at which you can resolve a given detail** by 1 + X/100. If you could read a sign at 30 feet, drawing +400% lets you read it at 150.

| Tap intensity | Acuity | What that looks like |
|---|---|---|
| +100% | ×2 range | Advantage on Wisdom (Perception) checks relying on that sense. |
| +400% | ×5 range | Read a page across a courtyard. Hear a conversation through a wall. Follow a trail by scent alone. |
| +900% | ×10 range | Pick one voice out of a crowded market. See the tremor in a distant hand. |
| +1,900% or more | ×20 range or better | Near-telescopic or near-microscopic. Count roof tiles a mile off, or find the hairline crack in a lock's face. |

}}

### Limits

Feruchemical tin **amplifies, it does not reveal**. Unlike Allomantic tin it grants no new way of sensing, and it will never show you what makes no impression at all: an invisible creature emits no light, so no amount of tapped sight will find one, though tapped hearing may still catch its step.

Tapping **sight** trades breadth for distance. Your vision narrows toward a binocular tunnel, so you lose peripheral awareness and have disadvantage on Perception checks to notice anything outside your focus. Tapping too much sight brings on nausea.

### Interactions

- Where Allomantic tin raises **all** senses at once and cannot be aimed, Feruchemical tin raises **one** sense as far as you like.
- A tin savant of the Allomantic art becomes dependent on the burn. Feruchemical storing has no such dependency, since nothing is drawn from outside you.

{{note

| | |
|---|---|
| **Attribute** | Senses, one per metalmind, including pain |
| **Storing** | That sense dulls toward absence; storing pain grants numbness at real risk |
| **Tapping** | Resolving range × (1 + intensity): ×5 at +400%, ×20 at +1,900% |
| **Limit** | Amplifies only what is already perceptible; tapped sight tunnels and sickens |

}}

\page

## Pewter: Brute

*A Brute spends a week thin and shaking, and buys with it an afternoon in which doors are suggestions and armored men are furniture.*

**Bloodline** Physical Ferring · **Metal** Pewter (91% tin, 9% lead) · **Attribute** Physical strength · **Capacity** 10 unit-minutes per gram

A **Brute** stores their own **physical strength** in a pewtermind. See the Ferring Bloodlines for the shared rules.

### Storing

While you fill a pewtermind, your muscles thin and weaken in proportion to what you store. You become frail, and may visibly shrink as muscle mass gives way.

- Reduce your effective Strength for checks, saves, attack damage, and carrying capacity by the fraction you are storing.
- At heavy storing you have disadvantage on Strength checks and saving throws, and lifting your own gear becomes a labor.
- Storing does not touch your base speed, your senses, or your wits. A storing Brute is weak, not slow or dull.

{{tableGroup

### Tapping

While you tap a pewtermind, your muscles swell far past their natural size and your strength with them.

**Your effective Strength equals your Strength score × (1 + the intensity you draw.)** Carrying capacity follows it directly, at 15 pounds per point as always. Your **body mass grows by half the intensity**, since the swelling is muscle and muscle is heavy.

| Tap intensity | Effective Strength | Carrying capacity | Body mass | Size |
|---|---|---|---|---|
| +100% | ×2 | ×2 | +50% | normal |
| +200% | ×3 | ×3 | +100% | count as one size larger to grapple, shove, and carry |
| +400% | ×5 | ×5 | +200% | **Large** |
| +900% | ×10 | ×10 | +450% | Large, and straining the frame that holds it |

}}

*Example.* A Brute with Strength 12 drawing +400% has an effective Strength of 60. They carry 900 pounds, and weigh three times what they did.

**The ceiling.** For **attack rolls and damage**, your Strength counts as no higher than **30**, however hard you draw. Past that point the extra force cannot reach the target: your grip fails, the weapon fails, or your footing gives before the blow does. Strength beyond 30 goes into **lifting, breaking, holding, and hurling**, where it has no ceiling at all.

### Limits

Strength is bounded by the body that carries it. At the highest tiers your **girth becomes its own problem**: while counting as Large, you have disadvantage on Dexterity (Stealth) checks and on checks to move through tight spaces, and you may simply not fit through a normal door. Your **clothing, armor, and gear do not grow with you**, so a Brute who taps hard mid-fight may burst straps and buckles.

Your added mass follows you everywhere. A heavily tapping Brute breaks chairs, founders in mud, and sinks in water, though the same weight makes them far harder to Steelpush; read your new weight on the force tables.

Your skeleton and joints are still yours. Tapping enormous strength lets you lift what your frame cannot survive lifting, and the DM is right to make you choose between the load and your own bones.

### Interactions

- Where Allomantic pewter is a fast, reactive burn with a Crash waiting at the end, Feruchemical pewter is patient: nothing is borrowed, so nothing comes due. What you spend is what you saved.

{{note

| | |
|---|---|
| **Attribute** | Physical strength |
| **Storing** | Frail and thin; reduced Strength, eventually disadvantage on Strength checks |
| **Tapping** | Effective Strength = score × (1 + intensity); mass grows by half the intensity; Large at +400% |
| **Ceiling** | Strength counts as at most 30 for attack and damage; lifting and breaking are uncapped |
| **Limit** | Girth, gear that does not grow, added mass, and a skeleton that still has limits |

}}

\page

### Cognitive

*Four metals for the mind, and for the machinery that keeps a body running.*

The Cognitive quadrant stores thought and regulation: mental speed into zinc, warmth into brass, memories into copper, wakefulness into bronze. Storing here costs you something a fight does not immediately notice, which makes it the quadrant that can be filled while the party sleeps or travels. Copper is the strange one, since a stored memory is genuinely gone from you until you tap it back, and an Archivist's coppermind is a library rather than a battery. Brass is the sole exception to Feruchemy's first rule: heat radiates, so a Firesoul is the only Ferring whose power reaches anyone but themselves.

::::

## Zinc: Sparker

*A Sparker spends the council meeting slack-jawed and dull, then taps the ring under the table and reads the whole room in the pause between two words.*

**Bloodline** Cognitive Ferring · **Metal** Zinc (pure) · **Attribute** Mental speed · **Capacity** 10 unit-minutes per gram

A **Sparker** stores their own **mental speed** in a zincmind. The attribute is the **rate at which you think**: tapping at +X% divides the time a mental task takes by 1 + X/100. See the Ferring Bloodlines for the shared rules.

### Storing

While you fill a zincmind, your thoughts thicken and slow. You are not stupid; you are simply late.

- Mental tasks take proportionally longer. A problem you would solve in a minute takes two while storing at 50%.
- At heavy storing you have disadvantage on Intelligence checks and on initiative.
- **You take in information normally.** Storing does not dull your senses or your memory. You hear the shout perfectly well; you are just slow to work out what it meant.

{{tableGroup

### Tapping

While you tap a zincmind, your thoughts race ahead of the world.

| Tap intensity | Effect |
|---|---|
| +100% | Mental tasks take half as long. Advantage on Intelligence checks and on initiative. |
| +400% | Mental tasks take a fifth as long. You gain **one additional reaction** each round, and you cannot be surprised. |
| +900% or more | You gain **one additional action** on each of your turns. You read a room, a page, or a fight faster than it can develop. |

}}

**The action ceiling.** One extra action is all zinc will ever give you, however hard you draw. Where steel grants a faster body, zinc grants a faster mind, and a full Feruchemist tapping both may hold two extra actions at once. No single attribute grants more.

### Limits

Speed of thought is not knowledge. You cannot reason your way to facts you do not have, and thinking about a locked door ten times faster opens nothing. A Sparker solves, plans, calculates, and notices; they do not divine.

Your **body still moves at its own pace**. Tapping hard means living in a world that has slowed to a crawl while your limbs answer at their usual speed, which is as maddening as it sounds. Long stretches at high intensity leave a Sparker impatient and short with everyone around them.

### Interactions

- No single Ferring taps both, but a full **Feruchemist** with zinc and steel is mind and body matched, quick in thought and quick in limb, and is the only way to hold two extra actions at once.
- Zinc is thought, not perception. To sharpen the senses themselves, that is Feruchemical tin.

{{note

| | |
|---|---|
| **Attribute** | Mental speed, the rate at which you think |
| **Storing** | Slow-witted and late, though your senses and memory are untouched |
| **Tapping** | Mental tasks take 1 ÷ (1 + intensity) as long; extra reaction, then one extra action |
| **Ceiling** | One extra action, ever |
| **Limit** | Faster thought is not more knowledge, and your body keeps its own pace |

}}

\page

## Brass: Firesoul

*A Firesoul walks into the flames and comes out cold, having drunk the fire down into a ring on their finger.*

**Bloodline** Cognitive Ferring · **Metal** Brass (about 75% copper, 25% zinc) · **Attribute** Warmth · **Capacity** 5,000 kJ per gram

A **Firesoul** stores **warmth** in a brassmind. See the Ferring Bloodlines for the shared rules, with the differences noted just below.

### How brass differs

Warmth is the one attribute a Ferring can draw from **outside** themselves, and it is the only one that is a plain physical quantity, **energy**. So brass sets aside two of the usual rules.

- It is measured in **kilojoules (kJ)**, not a percentage of yourself. A brassmind's charge is a number of kJ, and its capacity is fixed by mass rather than by unit-minutes.
- **There is no "hundred percent" ceiling.** Because the heat can come from a fire, a forge, or a river of lava, a Firesoul can store far more energy than their own body ever held.

Everything else follows the rules. Storing and tapping are free actions, a brassmind is keyed to your Identity, and compression still bites, harder than usual (see below).

{{tableGroup

### Throughput

Your level sets your **throughput**: the kilojoules per minute you can channel, in or out. It replaces the usual rate and depth.

| Level | Throughput | Enough to survive |
|---|---|---|
| 1 | 200 kJ/min | a campfire's warmth; a torch gripped briefly |
| 3 | 500 | a bonfire |
| 5 | 1,500 | a burning building, or being set aflame |
| 8 | 5,000 | a forge; a splash of molten metal |
| 12 | 15,000 | standing in open flame |
| 16 | 40,000 | **wading in lava** |
| 20 | 100,000 | swimming in lava |

}}

Throughput is a **hard limit while storing**, which is what gates survival, and your **free rate while tapping**, past which compression begins.

\column

### Storing: warmth in, and the cold that follows

While you fill a brassmind, heat flows out of you and into the metal. The trick every Firesoul learns is that **storing is the defense**: heat flows toward the cold, so a Firesoul drinking heat hard pulls a fire's warmth into their ring before it can harm them.

**Surviving heat.** Compare your throughput to the heat pouring off your surroundings.

- If your throughput **meets or beats** the incoming heat, you drink all of it. You stay at a healthy temperature and take no fire damage, however hot it is.
- If the heat **outpaces** your throughput, you drink what you can and the surplus cooks you. You take fire damage from the excess and begin climbing the Body Temperature table.

**The cold danger.** Storing is a defense only where there is heat to drink. Store hard with no source and you are draining your own body toward freezing. Each minute spent storing above your body's own output with nothing external to draw from, you slide *down* the Body Temperature table.

**The shock danger.** Beginning a hard store suddenly is its own risk. If you open a store at more than half your throughput in a single instant, make a Constitution saving throw against your Feruchemy save DC or fall **unconscious** from the shock.

{{tableGroup

### Body Temperature: the governor

Your body holds about 245 kilojoules for each degree Celsius, and it wants to sit at 37 °C. Heat you fail to store, or heat you strip away with nothing to replace it, moves you along this track. **Tapping never moves you here; you cannot cook yourself with your own warmth.** Only outside heat you failed to drink can overheat you.

| Off balance | Core temp | Effect |
|---|---|---|
| +1,200 kJ | 42 °C | Critical. Save or fall unconscious; death if it holds. |
| +740 kJ | 40 °C | Heatstroke. A level of Exhaustion and disadvantage. |
| +490 kJ | 39 °C | Feverish. Disadvantage on Constitution checks. |
| balanced | 37 °C | Fine. |
| −490 kJ | 35 °C | Chilled. Disadvantage; shivering. |
| −1,200 kJ | 32 °C | Hypothermia. A level of Exhaustion and disadvantage. |
| −2,200 kJ | 28 °C | Severe. Save or fall unconscious; death if it holds. |

}}

As a rule of thumb, each step is about **500 kJ** of surplus, gained or lost roughly one step per minute of serious imbalance. Return to balance and you recover the same way.

\page

{{tableGroup

### Tapping: warmth out

While you tap a brassmind, warmth pours back into you and out through your skin. Running hot is its own shield: heat flows only from hot to cold, so a fire no hotter than you have made yourself has no warmth left to give.

| Tap intensity | Effect |
|---|---|
| +100% | Feverishly warm. You ignore cold weather and have **resistance to cold damage**. Snow melts where you stand. |
| +400% | **Immunity to cold damage.** You warm a room, dry soaked clothing, thaw a lock, and scorch cloth held against you. You run as hot as open flame: **immune to fire from nonmagical sources and from magical fire no hotter than ordinary flame.** A creature that touches, grapples, or starts its turn within 5 feet of you takes **1d6 fire damage.** |
| +900% | Forge-hot. You set light to dry things you touch and can soften metal in your grip. Your fire immunity covers all but the hottest magical flame. Radiant damage rises to **2d6.** |
| +1,900% or more | Hotter than any natural fire, immune to all but the truly extraordinary. Radiant damage caps at **4d6** and climbs no further. Excess pours off as blinding light and shimmering air; a Firesoul is a furnace, not a growing bomb. |

}}

**Melting and igniting** take **sustained, focused contact**, not an instant, because you can only pour so much heat into one small thing at a time. Setting a rope alight is immediate; softening a lock is a round or two of grip; melting through a steel bar is the work of many rounds, or a Compounder's.

{{tableGroup

#### Compression runs harsh

Released energy is potent even for a heartbeat, so brass loses it fast when you force it out faster than your throughput. Divide the kilojoules per minute you want by your throughput to get the multiple, then read your recovery.

| Multiple of throughput | 1× | 2× | 3× | 4× | 5× |
|---|---|---|---|---|---|
| **Recovery** | 1.00 | 0.50 | 0.25 | 0.13 | 0.06 |

}}

Recovery **halves** with each multiple, far steeper than the 0.8 of other metals. A Firesoul who dumps everything at once to melt a door in a single round may burn through ten times the energy they actually deliver. Bursting is possible; it is simply ruinous to your reserve.

### Limits

**The metalmind is exposed.** A brassmind does not itself run hot or cold; it is a battery, not a coal. But it is still metal in the world. A Firesoul wading through lava with a bare ring may have it **melt away**, and losing the metalmind loses everything in it and every defense at once. A heavily charged metalmind resists heat and harm far better than an empty one, so a deep store is partly its own armor, but a Firesoul who means to walk through fire keeps their metalminds embedded or shielded.

Warmth is not fuel. It keeps you from freezing and lets you set things alight, but it will not feed you, wake you, or heal you.

### Interactions

- Storing warmth is one of the few Feruchemical defenses that works **while filling**, which makes a Firesoul strongest exactly as they build their reserve.

{{note

| | |
|---|---|
| **Attribute** | Warmth, measured in kilojoules |
| **Scale** | kJ contents, level-gated throughput (kJ/min), no percent-of-self cap |
| **Storing** | Drink incoming heat up to throughput to stay unharmed; over-store with no source and you freeze |
| **Governor** | Body Temperature table; tapping never overheats you |
| **Tapping** | Cold resistance, then immunity, then radiant fire (capped 4d6); melting takes sustained contact |
| **Compression** | Harsh: recovery halves per multiple of throughput |

}}

\page

## Copper: Archivist

*An Archivist can recite a book they have never read twice, and can look their own brother in the face without knowing him. Both are the same ring.*

**Bloodline** Cognitive Ferring · **Metal** Copper (pure) · **Attribute** Memories · **Capacity** 5 memories per gram

An **Archivist** stores their **memories** in a coppermind. See the Ferring Bloodlines for the shared rules, with one large exception noted below.

### Copper does not work like the others

Every other metal stores an attribute as a quantity across time, and everything about rate, depth, and compression follows from that. **Copper does not.** A memory is a discrete thing. It is either in your head or in the metal.

- There is **no intensity** and **no duration**. You do not store memory at 40% for an hour.
- Capacity is counted in **memories, not unit-minutes**: a coppermind holds **5 memories per gram**, so a 5-gram ring holds 25.
- Your **rate** and **depth** do not apply. Compression never touches a coppermind, and a memory drawn out at 20th level is exactly the memory a 1st-level Archivist put in.

A "memory" is one coherent thing. As a rule of thumb, one memory is as much as you could attentively take in at a single sitting: a conversation, a face, an afternoon, the contents of a page, the route through a city. A trained mind can bundle far more into a single memory. A **Keeper**, drilled in the art since childhood, may hold an entire book, a genealogy, or a day's events as one coherent piece. Where a character falls on that scale is theirs to establish and the DM's to rule on.

### Storing

Storing a memory takes an **action**. When it is done, **the memory is gone from you**. You retain the knowledge of where you stored the memory along with an idea of what it was for a short time, but that fades quickly too.

- You may store a memory **partially**, keeping a vague recollection of it. The copy in the metal is correspondingly weaker and blurred.
- Memories in a coppermind **never degrade**. One stored forty years ago comes back as sharp as the day it went in, while the memories still in your head fade as anyone's do.

### Tapping

Tapping draws a memory back out and into your mind, where you experience it with the clarity of the moment it was stored. Afterward you may store it again, or simply let it stay with you.

- **Perfect recall.** A memory retrieved from copper is not reconstructed, it is returned. You can read back a page you stored word for word.
- **Study.** An Archivist can commit a library to metal a page at a time and carry it on one hand.
- **Advantage** on any check to recall information you have deliberately stored.

### Index copperminds

Because a stored memory leaves no trace of itself, a working Archivist keeps an **index**: one coppermind holding the memory of what is in all the others. Losing your index is the particular nightmare, since you are left holding a fistful of rings and no idea what any of them contain, without withdrawing each memory again.

### Limits

- **Memories are not skills.** Storing your memory of a duel does not take away your ability to fence, and tapping it will not teach fencing to anyone else. Copper holds what you knew and saw, not what your hands learned.
- **Only your own.** You cannot store another person's memories, nor read theirs from a mind they filled, unless that mind was filled **unsealed** to begin with, which requires the filler to have stored their own Identity as they filled it.
- **The loss is real.** An Archivist who stores too freely can walk past their own child and feel nothing but a vague sense that something is missing. Used carelessly, copper is how a person misplaces themselves.
- **It is also a defense.** What is not in your head cannot be taken from it by torture, by charm, or by any power that reads a mind. Terris stewards carried secrets this way for centuries.

{{note

| | |
|---|---|
| **Attribute** | Memories, stored whole |
| **Capacity** | 5 memories per gram, not unit-minutes |
| **Storing** | An action; the memory leaves you entirely, or partially for a blurred copy |
| **Tapping** | Perfect recall, exactly as stored, with no decay ever |
| **Exception** | Rate, depth, and compression do not apply to copper at all |
| **Limit** | Not skills, only your own memories, and forgetting is genuine |

}}

\page

## Bronze: Sentry

*A Sentry sleeps a long, dreamless winter into a bracelet, and spends it standing watch through a siege without once sitting down.*

**Bloodline** Cognitive Ferring · **Metal** Bronze (88% copper, 12% tin) · **Attribute** Wakefulness · **Capacity** 10 unit-minutes per gram

A **Sentry** stores their own **wakefulness** in a bronzemind. The quantity is **alert waking time**: how long you can be awake, and how sharply. See the Ferring Bloodlines for the shared rules.

### Storing

While you fill a bronzemind, you grow drowsy, and at depth you sink into a slow, dreamless, trance-like sleep.

- At light storing you are simply tired: disadvantage on Perception checks and on initiative.
- At heavy storing you are barely rousable, and sleep gives you **reduced benefit**. You need a longer rest than usual to gain the effects of a long rest.
- **Bronze is the one metalmind you can fill while asleep.** This is the whole art of the Sentry: an ordinary night's sleep, spent storing, banks wakefulness rather than wasting it.

**Storing through a rest.** When you sleep while storing at intensity `s`, that fraction of the rest is banked and only the remainder counts as actual rest.

- At **50%**, an 8-hour sleep gives the benefit of a 4-hour rest (treat it as a short rest) and banks the other four hours' worth.
- At **10%**, you lose almost nothing: sleep about 10% longer than usual and you still gain a full long rest while banking the surplus.
- At **100%**, you gain no rest at all; the entire sleep is stored.
- To gain a full long rest while storing, sleep **1 ÷ (1 − s)** times as long: a little longer at low intensity, twice as long at 50%.

You may also simply oversleep on purpose to bank the extra. A Sentry can even enter a trance and store for days on end to lay in a great reserve at once, though it leaves them helpless throughout and is rarely wise.

\column

{{tableGroup

### Tapping

While you tap a bronzemind, sleep stops mattering.

| Tap intensity | Effect |
|---|---|
| +100% | You need no sleep while you tap, and you have advantage on Wisdom (Perception) checks to notice what is around you. |
| +400% | You cannot be **surprised**, and you have advantage on initiative. Long watches cost you nothing. |
| +900% or more | Preternatural alertness. You notice every change in a room the moment it happens, and cannot be caught unaware by anything you could conceivably perceive. |

}}

**Rest.** Tapping bronze for the length of a long rest grants you the **benefits of that long rest without sleeping**, so long as you keep tapping throughout. Stop tapping, and the accumulated tiredness arrives at once: you must sleep at the first opportunity or begin gaining Exhaustion at the DM's discretion.

### Limits

**Wakefulness is not energy.** Bronze keeps you awake and alert; it does not feed, heal, or rest the body. A Sentry who has gone a week without sleep is clear-eyed and sharp, and still starving, still sore, still hurt. Alertness cannot carry a body its own strength will not.

**Stimulants can be banked.** Caffeine and similar drugs generate wakefulness you did not have, and a Sentry may store that too. Tapped back later it feels wrong: jittery, thin, and hard to think through, though it does keep you upright.

### Interactions

- The Sentry's economy is unusually kind. Every other Ferring pays for their reserve with hours of being diminished while awake. A Sentry pays with **sleep they were going to spend anyway**, but simply without the usual benefits of that sleep.

{{note

| | |
|---|---|
| **Attribute** | Wakefulness, alert waking time |
| **Storing** | Drowsy, then trance-like; sleep gives reduced benefit. **Fillable while asleep** |
| **Tapping** | No need for sleep, then no surprise, then total alertness |
| **Rest** | Tapping through a long rest grants its benefits without sleeping |
| **Limit** | Keeps you awake, never fed, healed, or rested in body |

}}

\page

### Hybrid

*Four metals for the processes that keep you alive between one moment and the next.*

The Hybrid quadrant sits between body and spirit, storing breath into cadmium, nutrition into bendalloy, health into gold, and determination into electrum. These are the metals of endurance rather than of a single decisive moment: air for a room that has none, a meal for a week without one, a wound closed while someone is still swinging at you. Gold is the famous one and the most easily overspent, since tapping health faster than you stored it is how a Bloodmaker walks out of something that should have killed them and then cannot stand up afterward.

::::

## Cadmium: Gasper

*A Gasper takes a few deep breaths at the water's edge, then walks in and keeps walking, across the bottom, for as long as the ring on their finger holds air.*

**Bloodline** Hybrid Ferring · **Metal** Cadmium (pure) · **Attribute** Breath · **Capacity** 5 minutes of breathing per gram

A **Gasper** stores **breath** in a cadmiummind. Breath is a **reserve**, not an intensity: a cadmiummind holds minutes of breathing, banked now and spent later, the way copper holds memories rather than a percentage. See the Ferring Bloodlines for the shared rules.

### Storing

A cadmiummind holds breath measured in **minutes of resting breathing**, up to its capacity of 5 minutes per gram. While you fill one, you must **breathe hard and fast**, banking the surplus.

- Breathing at roughly twice the normal rate banks about **1 minute of reserve for each minute you keep it up**. It is loud, obvious, and impossible to do quietly.
- Breathing **rich or pressurized air**, a deep-diver's trick, doubles the rate to about 2 minutes of reserve per minute.
- **Over-breathing.** Push faster than that and you court a blackout. At the end of each minute you bank faster than one minute of reserve per minute, make a Constitution saving throw against your Feruchemy save DC or grow dizzy and fall **unconscious** from hyperventilation.

So a Gasper filling a 40-minute reserve spends the better part of an hour breathing like a bellows, or half that on bottled, pressurized air before a dive.

### Tapping

While you tap a cadmiummind, your blood stays oxygenated without your drawing a single breath.

- At rest or light activity, one minute of reserve buys about **one minute** of not breathing.
- Hard exertion burns air far faster. Strenuous activity, such as fighting or swimming for your life, spends reserve about **four times as fast**, so a lungful banked is only a minute or two of desperate struggle underwater.

- You can go **without breathing**: underwater, in smoke or gas, in a sealed vault, in a vacuum's want of air.
- Because you are not breathing, you do not draw in what surrounds you. Poisoned air, spores, and smoke have nothing to enter by while you tap.
- **Over-oxygenation.** Tapping while you can still breathe floods your blood with more oxygen than a body normally holds. You ignore the effects of thin air and high altitude, and you have advantage on Constitution checks and saving throws to keep going through hard, sustained exertion.

### Limits

Cadmium gives you **air, and only air**. It does not shield you from water pressure at depth, from the cold of the sea or the void, or from the simple fact of drowning if you panic and inhale. A Gasper crossing a river bottom still needs to keep their mouth shut; the ring means they will not suffocate, not that they cannot.

Breath is not energy, food, or wakefulness. You can go without air, and still starve, still tire, still freeze.

### Interactions

- A Gasper is the quiet answer to a great many death traps: gas, flood, smoke, the airless dark. Its weakness is that filling is loud and obvious, so a reserve must be laid in ahead of need.

{{note

| | |
|---|---|
| **Attribute** | Breath, a reserve measured in minutes |
| **Storing** | Breathe hard to bank air; fast filling risks a hyperventilation blackout |
| **Tapping** | Go without breathing; breathe nothing harmful; over-oxygenate to beat altitude and exertion |
| **Limit** | Air only, not pressure, not drowning, not food or rest |

}}

\page

## Bendalloy: Subsumer

*A Subsumer eats like three field hands through the autumn, and crosses the winter desert on a ring, never once stopping to open a pack.*

**Bloodline** Hybrid Ferring · **Metal** Bendalloy (50% bismuth, 26% lead, 14% tin, 10% cadmium) · **Attribute** Nutrition · **Capacity** 2 days of sustenance per gram

A **Subsumer** stores **nourishment** in a bendalloymind. Like breath, it is a **reserve** rather than an intensity: the mind holds days of sustenance, banked now and spent later. See the Ferring Bloodlines for the shared rules.

### One need to a metalmind

A single bendalloymind stores **calories**, the body's food. Other needs take their own metalminds, filled the same way:

- a separate mind for **water**,
- and, for creatures that live on stranger fare, a mind for whatever they consume: sunlight for a person of green things, blood, or salt for others.

You wear a bendalloymind the way a traveller packs a larder, one ring per thing you cannot do without.

### Storing

A bendalloymind holds sustenance measured in **days**, up to its capacity of 2 days per gram. *(One day is roughly 2,000 kilocalories for anyone who prefers to count them, but days are far easier at the table.)*

While you fill one, the mind swallows what you eat before your body can. You can consume **far more than should be possible**, meal after meal, without filling up or gaining an ounce, and you stay hungry the whole time, since almost nothing reaches you.

- A determined day of gorging, eating three or four times what you need, banks a **few days** of reserve. You can only eat so fast, so a great store is the work of many such days.
- Water fills the same way: drink and drink, stay thirsty, and fill a watermind.

### Tapping

While you tap a bendalloymind, your body is nourished as though you had eaten a proper meal, though your stomach stays empty. You draw a day of sustenance for each day you go without, at whatever pace your body needs.

- You can go **without eating or drinking** for as long as the reserve lasts, crossing deserts, waiting out sieges, or enduring a cell that offers nothing.
- A hard draw can shake off the drag of hunger or thirst already on you: spend from the mind to end the effects of starvation or dehydration you have already suffered.

### Limits

Bendalloy feeds you; it does not power you. It grants no burst of strength, no extra action, no hit points. It answers hunger and thirst, and nothing else. A well-fed Subsumer with an empty everything-else still tires, still suffocates, still bleeds.

Filling is bounded by your own body. You can only eat so fast and hold so much at once, so a great reserve is the work of days of determined gorging, not an afternoon.

### Interactions

- Bendalloy, cadmium, and bronze together answer nearly every slow death: hunger, thirst, airlessness, and exhaustion. No single Ferring holds more than one of them, but a full **Feruchemist** wearing all three can cross a wasteland that would kill anyone else.

{{note

| | |
|---|---|
| **Attribute** | Nutrition, a reserve measured in days; one need per metalmind |
| **Storing** | Eat or drink far past your fill without gain, banking it; you stay hungry |
| **Tapping** | Go without food or water; end hunger or thirst already suffered |
| **Limit** | Sustenance only, no strength, no HP, no wakefulness |

}}

\page

## Gold: Bloodmaker

*A Bloodmaker takes the wound that should have killed them, staggers, and stands back up with the skin already closing, paid for out of a ring bought with weeks of being sick.*

**Bloodline** Hybrid Ferring · **Metal** Gold (pure) · **Attribute** Health · **Capacity** 10 hit points per gram

A **Bloodmaker** stores their own **health** in a goldmind. Like brass, gold sets aside the percentage frame for a concrete unit: a goldmind's charge is a number of **hit points** of healing, banked while sick and spent to mend. See the Ferring Bloodlines for the shared rules.

### Storing

While you fill a goldmind, you grow **ill**. Your body pours its vigor into the metal instead of into keeping you well, and you feel every bit of it. There are two ways to fill.

**Redirecting healing.** While you are storing and awake, any hit points you would regain, from Hit Dice, a potion, or a spell, pour into the goldmind instead of into you. You **cannot** store during a **long rest**, because you must be awake to store, so a night's sleep still heals you normally.

**Deliberate storing.** You may bank health directly, in committed stretches of **10 minutes**. Choose a rate in hit points per 10 minutes. For as long as you store, you take a **penalty to all Constitution checks and saving throws equal to that rate**, as the sickness settles in. If you break off before a 10-minute stretch is done, nothing is stored for it.

Your body will give only so much before it starts giving too much. Your **safe rate is 5 + your Constitution modifier** hit points per 10 minutes. Store faster, and for each point beyond your safe rate you take **1 damage per 10 minutes** as your body begins to eat itself to fill the ring.

*So a Bloodmaker with a +0 Constitution modifier banks up to 5 hit points per 10 minutes at a cost of −5 to all Constitution checks and saves. A hardy one with +5 banks up to 10, at −10. Either could push past their limit, and pay for it in blood.*

### Tapping

While you tap a goldmind, your flesh knits, your blood replenishes, and wounds close before your eyes. Gold does three things, along three separate lanes.

**Reactive healing.** On your turn, or in response to taking damage, draw hit points from the goldmind to heal yourself, up to a **free rate of (your Constitution score ÷ 4) + your proficiency bonus** hit points per round. Constitution is how much your body can take in at once; proficiency is your growing skill at guiding it. You may heal *faster* in a crisis, paying compression (below).

**Slow mending.** Patience is rewarded. Whenever you finish a **short rest** with a charged goldmind, you regain **bonus hit points equal to your proficiency bonus**, drawn from the ring, on top of any Hit Dice you spend. Hit points gained from tapping gold, here or anywhere, are Feruchemically made and **can never be stored back into a goldmind**; there is no perpetual well.

**Surviving a killing blow.** While you have a charged goldmind, you need not fall. If damage would drop you below 0 hit points, you may pay from the ring to stay at **0 hit points, conscious and able to act**, at a cost of **2 hit points from the ring for each 1 by which you were driven below 0**. You weather blows that would kill an ordinary person where they stand, for exactly as long as the gold pays. The instant the ring cannot cover a blow in full, it fails, and that blow drops you as it normally would.

{{tableGroup

#### Compression

When you heal faster than your free rate, divide the rate you want by your free rate to get the multiple, then read your recovery, on the standard curve.

| Multiple of free rate | 1× | 2× | 3× | 4× | 5× |
|---|---|---|---|---|---|
| **Recovery** | 1.00 | 0.80 | 0.64 | 0.51 | 0.41 |

}}

Gold's teeth are not here but in the other two lanes: the **sickness of storing** and the flat **2-for-1** of cheating death. Ordinary healing is merely metered.

### Limits

Gold heals the **body toward its ideal self**, and no further. This is the source of every limit.

- **It cannot fix what the body was born as.** Genetic conditions, missing pieces you never had, and the slow work of age are the body's ideal, not a wound to it. Gold will not touch them.
- **It cannot heal the soul or the mind.** Damage to the spirit or the Cognitive self is beyond it. Gold mends flesh.
- **It heals over, not out.** A foreign thing left in a wound, an arrowhead, a bullet, a blade, is sealed inside as the flesh closes. Remove it first, or the wound will mend around it and you will carry it. **Aluminum** held in a wound stops the healing there entirely.
- **Regrowth is dear.** Restoring a lost limb or a ruined organ is possible, but costs a great deal of stored health and time, not a round's worth.

{{note

| | |
|---|---|
| **Attribute** | Health, measured in hit points |
| **Storing** | Redirect short-rest Hit Dice, or store deliberately at −(rate) to Con checks/saves; safe rate 5 + Con mod, self-damage beyond |
| **Tapping** | Heal (Con÷4 + prof)/round free; short-rest bonus = prof; or stay at 0 HP past a killing blow at 2 ring-HP per 1 overkill |
| **Limit** | Mends flesh toward its ideal only: no genetics, no soul, foreign objects seal in, aluminum blocks it |

}}

\page

## Electrum: Pinnacle

*A Pinnacle spends the calm days grey and listless, then taps the ring when the walls are falling and becomes a person who simply will not stop.*

**Bloodline** Hybrid Ferring · **Metal** Electrum (about 45% gold, 55% silver) · **Attribute** Determination · **Capacity** 10 unit-minutes per gram

A **Pinnacle** stores their own **determination** in an electrummind: the will to press on, to hold a line, to refuse to break. This is one of the least-understood attributes in Feruchemy, and much of what follows is careful extrapolation rather than settled lore. The attribute scales like most, tapping at +X% multiplying your drive. See the Ferring Bloodlines for the shared rules.

### Storing

While you fill an electrummind, your will drains away and a grey **listlessness** settles over you. You are not sad so much as emptied of the wish to do anything at all.

- Reduce your resolve in proportion to what you store. You have disadvantage on saving throws against being Frightened, Charmed, or otherwise cowed or swayed.
- At heavy storing you struggle to act on your own initiative, needing prompting or orders to do more than the minimal, at the DM's discretion. You are not incapable, only unwilling.
- Storing does not touch your body or your wits. A storing Pinnacle is listless, not weak or slow or stupid.

{{tableGroup

### Tapping

While you tap an electrummind, a fierce, rising drive fills you, and at the top it becomes a mania nothing can turn aside.

| Tap intensity | Effect |
|---|---|
| +100% | Advantage on saving throws against being Frightened or Charmed, and against effects that would sway or command you. |
| +400% | You are **immune** to the Frightened and Charmed conditions, and to fear and morale effects. Pain and despair do not slow you. |
| +900% or more | Unbreakable. You have advantage on any saving throw to avoid being forced to stop acting, and you may ignore effects that would make you flee, surrender, or stand down. You keep going where any reasonable person would break. |

}}

### Limits

**Will is not skill.** Determination makes you refuse to fail; it does not make you succeed. You gain no bonus to attack, to checks, or to damage. A Pinnacle who will not stop trying to pick a lock is exactly as good at picking it as before, only unwilling to walk away.

**Mania has its own price.** At high intensity you cannot easily be made to do the sensible thing. Retreating from a hopeless fight, abandoning a doomed plan, or standing down when you should are themselves choices a driven Pinnacle may be unable to make. The DM may rule that while tapping heavily you must have a genuine reason before you can disengage, flee, or give up a course of action.

**Storing is dangerous.** A Pinnacle who banks too much of their will can be talked, frightened, or led into almost anything, and may lack the drive to save themselves from it.

### Interactions

- Determination pairs naturally with anything that punishes fear or hesitation. A Pinnacle holds the line that others break from.
- So little of electrum's Feruchemy is settled in lore that a table should feel free to shape the details to their game. What is firm is the shape: listless while storing, unstoppable while tapping.

{{note

| | |
|---|---|
| **Attribute** | Determination, the will to continue |
| **Storing** | Listless and easily swayed; disadvantage against fear and charm |
| **Tapping** | Advantage, then immunity to fear and charm, then an unbreakable refusal to stop |
| **Limit** | Will is not skill, and mania can keep you from the sensible retreat |

}}

\page

### Spiritual

*Four metals for what a person is, rather than what their body does.*

The Spiritual quadrant is the strangest and the least understood, storing Fortune into chromium, Investiture into nicrosil, Identity into aluminum, and Connection into duralumin. What these do is hard to state as a number and harder to adjudicate at speed, and any table using them should expect to talk through the first few uses. They are also the quadrant that makes the rest of the system possible: an unsealed metalmind, which anyone may draw from, requires a Trueself's stored Identity, and Compounding leans on this quadrant more than any other.

::::

## Chromium: Spinner

*A Spinner spends a grey week where nothing goes right, and buys with it a single moment where nothing can go wrong.*

**Bloodline** Spiritual Ferring · **Metal** Chromium (pure) · **Attribute** Fortune · **Capacity** 1 Fortune point per gram

A **Spinner** stores **Fortune**, the raw luck of the world, in a chromiummind. Fortune is a **reserve** measured in **Fortune points**, banked by suffering misfortune and spent to bend chance your way. The Spiritual metals are the least understood in all of Feruchemy, and chromium most of all; treat what follows as a working translation, not settled law. See the Ferring Bloodlines for the shared rules.

### Storing

While you fill a chromiummind, luck drains out of you and the small cruelties of the world find you out. Ropes fray, footing slips, the guard glances up at the wrong moment.

- While storing, you have **disadvantage on all d20 tests**. You are simply, spiritually unlucky.
- For each **10 minutes** you spend storing, you bank **1 Fortune point**, to your metalmind's capacity.
- A Spinner laying in a reserve is a miserable thing to be near, and knows it.

### Tapping

While you tap a chromiummind, chance leans your way, and the same small coincidences that plagued you now save you. Tapping is not a state you maintain but a thing you spend, point by point.

- **Spend 1 point** to reroll a d20 you just rolled and use the new result, or to force a creature you can see to reroll a d20 and use the lower result.
- **Spend 2 points** to give yourself advantage on a roll before you make it, or to turn a coincidence firmly in your favor: a rope where you need one, a distracted sentry, a loose stone underfoot for your enemy.
- **Spend 3 or more points** to bend a larger stroke of luck, at the DM's discretion. Fortune does not break the laws of the world; it only chooses, among the things that could happen, the ones that help you.

You may spend Fortune points from a chromiummind at any time, even in response to a roll, without an action.

### Limits

**Fortune is chance, not power.** It cannot make a thing happen that could not have happened anyway. A locked door with no key and no flaw stays locked; luck finds the flaw that was already there, or it finds nothing.

**The reserve is dear.** Ten minutes of being cursed for a single reroll is a hard trade, and it is meant to be. A Spinner hoards luck for the moment that matters and lives a little unluckier the rest of the time.

### Interactions

- Allomantic and Hemalurgic chromium do very different things; this is the Feruchemical art alone, the storing of one's own Fortune.

{{note

| | |
|---|---|
| **Attribute** | Fortune, a reserve measured in luck points |
| **Storing** | Disadvantage on all d20 tests; bank 1 point per 10 minutes |
| **Tapping** | Spend points to reroll, force enemy rerolls, gain advantage, or turn a coincidence |
| **Limit** | Luck finds a flaw that exists; it cannot invent one |

}}

\page

## Nicrosil: Soulbearer

*A Soulbearer sets their magic aside into a ring, walks a while as an ordinary person, then draws it back and casts higher than they ever could unaided.*

**Bloodline** Spiritual Ferring · **Metal** Nicrosil (85% tin, 15% chromium) · **Attribute** Investiture · **Capacity** see below

A **Soulbearer** stores **Investiture**, the raw stuff of magic, in a nicrosilmind. Even the Terris who use it admit they do not fully understand it. See the Ferring Bloodlines for the shared rules,.

### What nicrosil stores

Nicrosil holds the **ability to wield a magical art**, not that art's fruits. It does not store strength, or speed, or fire. It stores the *power to use* a given Invested art. Store your spellcasting and you hold the **ability to cast**, not a stack of finished spells. A full Feruchemist storing one of their other metals banks the **ability to store and tap that metal**, not the strength or speed it grants.

**One ability to a metalmind, and while it is stored you cannot use it.** Bank your spellcasting and you cannot cast a thing until you draw it back.

### Storing

Set an ability aside into a nicrosilmind. You go without it entirely for as long as it is stored, the usual Feruchemical trade: give up now, to have more later.

For a caster, choose how the mind is **keyed** when you begin. This is a choice for your table:

- **Keyed to one spell.** The mind holds your ability to cast a single spell you know. Narrow, and the safer choice, especially for anything ever meant to leave your own hand.
- **Keyed to your casting.** The mind holds your spellcasting at large, any spell you know. More useful to you, and the reason the cap below matters.

### Tapping, for yourself

Draw the ability back and wield it **magnified**. While tapping, you may reach past your own ceiling: cast a spell you know using a slot **higher than the highest you could normally manage**, the extra levels paid out of the ring. Push only a step past your limit and the mind lasts a while; reach far beyond it and compression empties it fast.

\column

### Sharing is a Feruchemist's art, not a Ferring's

A lone Soulbearer can only ever tap **their own** minds. For another creature to tap a nicrosilmind and cast your spells though they never learned a word of them, that mind must be **unsealed**, which means it must be filled **from its very first charge** while your own **Identity** is fully stored in aluminum. A mind cannot be unsealed after the fact; the key goes on as it is filled and never comes off. That means being a **full Feruchemist**, with two metals and the class, not a single-bloodline Ferring.

So handing magic person to person is real, and it is the strongest thing nicrosil can do, but it is gated behind **two metals and a class**, and remains firmly the DM's call: bounded in time, limited to the one stored ability, and never a quiet upgrade for a whole party.

### Limits

- **One ability, wholly gone while stored.** You do not keep a lesser version; you cannot use it at all until you draw it back.
- Nicrosil **moves** the power to wield magic; it makes none. You can bank only what you already had, and it grants no spell you did not know.

{{note

| | |
|---|---|
| **Attribute** | Investiture, the ability to wield one magical art, one per metalmind |
| **Storing** | Set the ability aside (you cannot use it); key a casting mind to one spell or to your casting at large |
| **Tapping** | Restore it and magnify: upcast past your normal ceiling, capped |
| **Sharing** | Only a **Feruchemist** (nicrosil + aluminum) can fill a mind unsealed from the first charge, for another to wield; DM-gated |
| **Risk** | The highest-variance metal; capacity and magnify caps are important |

}}

\page

## Aluminum: Trueself

*A Trueself can hollow themselves out until they are no one at all, or draw so fully into themselves that nothing which rewrites a person can find purchase.*

**Bloodline** Spiritual Ferring · **Metal** Aluminum (pure) · **Attribute** Identity · **Capacity** 10 unit-minutes per gram

A **Trueself** stores their **Identity**, the spiritual sense of being *themselves and no other*, in an aluminummind. This is among the least-understood powers in Feruchemy, rarely spoken of even among the Terris. It scales like an intensity, storing toward *blankness* and tapping toward an unbreakable sense of self. See the Ferring Bloodlines for the shared rules.

### Storing: becoming no one

While you fill an aluminummind, your sense of self thins, and you become a blank slate. This is unsettling and dangerous, and it is also the root of Feruchemy's most useful trick.

- **Unsealed metalminds.** Any metalmind you fill **while your Identity is fully stored** carries no owner: it is **unsealed**, and anyone with the matching power may tap it. For a lone Trueself this matters little, since your only metalminds are aluminumminds. Its real weight is in the hands of a **Feruchemist**, who can fill a *pewtermind* of strength, a *goldmind* of health, or a nicrosilmind of spellcasting this way and hand it to someone else. Note that this works only **as the mind is filled**: a mind already keyed to you cannot be hollowed out and unsealed later. Aluminum is the reason unsealed metalminds exist at all.
- **Borrowing another's minds.** With your Identity **fully stored**, you carry no self to clash with the lock on someone else's metalmind, and you may tap their minds, friend or foe, as though they were your own. But you can only ever draw out a power **you could already wield**: to drain a foe's banked strength, you must be able to tap a pewtermind yourself. So this is a Feruchemist's reach, needing **aluminum to empty your Identity and the matching metal to use what you find**.
- **A self too faint to find.** With no Identity, effects that reach for *you* by name or by soul, scrying, some divinations, a curse laid on your true self, may simply fail to find anyone there.
- **The cost.** Identity is what makes a spiritweb *yours*, and what magic checks against when it tries to rewrite one. Emptied of it, you are a blank canvas: not more easily persuaded, but more easily **overwritten**. While heavily storing you have **disadvantage on saving throws** against effects that remake what you are, meaning possession, permanent transformation, and anything that rewrites your history or nature outright. Your judgement is untouched. It is your self that has no edges.

{{tableGroup

### Tapping: becoming wholly yourself

While you tap an aluminummind, you become intensely, unshakably *you*.

| Tap intensity | Effect |
|---|---|
| +100% | Advantage on saving throws against possession, transformation, and any effect that would rewrite what you are. |
| +400% | You **cannot be transformed, disguised over, or possessed** against your will, and illusions and Forgeries slide off your true shape. You may end one such effect already on you. |
| +900% or more | Your self is adamant. You are immune to possession and unwilling transformation, and you may **mend damage to your own mind**: end a madness, a curse of the personality, or an alteration to who you are, restoring the self you know yourself to be. |

}}

### Limits

- Identity mends the *self*, not the flesh or the mind's knowledge. It will not heal a wound or return a lost memory; it returns *who you are* when something has tried to make you otherwise.
- **Draining another's minds is a Feruchemist's feat, not a snatch-and-grab.** You *can* tap a keyed mind that is not yours, but only by fully emptying your own Identity first, and only to use a power you could already wield yourself. A lone Trueself, with no other metal to their name, empties their self to no such purpose; they can blank the lock, but have no way to use what lies behind it.

### Interactions

- Aluminum is the metal that makes **unsealed metalminds** possible, which the whole of nicrosil's hand-me-down magic and much of Compounding with unkeyed minds depends upon.

{{note

| | |
|---|---|
| **Attribute** | Identity, the spiritual sense of self |
| **Storing** | Become a blank: minds you fill while hollow are born unsealed, tap others' keyed minds (for powers you can already use), fade from identity-seeking magic |
| **Tapping** | Become adamant: resist then refuse alteration; at the peak, heal damage to your own mind |
| **Limit** | Mends the self only, not flesh or memory; emptying yourself is truly dangerous |

}}

\page

## Duralumin: Connector

*A Connector can walk through a hostile court and have no one quite remember they were there, or sit down among strangers who speak no tongue they know and rise an hour later as a trusted friend.*

**Bloodline** Spiritual Ferring · **Metal** Duralumin (96% aluminum, 4% copper) · **Attribute** Connection · **Capacity** 10 unit-minutes per gram

A **Connector** stores **Connection**, the web of bonds that ties a person to others, to places, and to the world itself, in a duraluminmind. It scales like an intensity, storing toward being *unnoticed* and tapping toward being *instantly, deeply known*. See the Ferring Bloodlines for the shared rules.

### Storing: fading from the world

While you fill a duraluminmind, the threads that connect you to those around you go slack. People's attention slides off you, and their regard cools.

- At light storing, you are simply forgettable and easy to overlook.
- At heavy storing, attention **actively avoids** you: you have advantage on Dexterity (Stealth) checks to go unnoticed even in the open, witnesses struggle to recall you, and a creature must have real reason to single you out. This is not invisibility; you are plainly there, and no one cares to notice.
- The same fading makes you a stranger to everyone. While storing, you have **disadvantage on Charisma checks** to persuade, charm, or be believed. No one is inclined to connect with someone the world has forgotten.

{{tableGroup

### Tapping: belonging at once

While you tap a duraluminmind, bonds form in moments that would normally take months. This is **not** the *charm* spell; the trust you build is real, and it lasts, though the deeper effects fade when you stop tapping.

| Tap intensity | Effect |
|---|---|
| +100% | Advantage on Charisma (Persuasion) checks to build rapport, and you may improve a creature's attitude toward you a step faster than talk alone would allow. |
| +400% | You **belong here.** You speak and understand the **local language** for as long as you tap, and you carry yourself as a native of this place, its customs and manners suddenly known to you. You can pass as a local among locals. |
| +900% or more | You form a **true, lasting bond** with a person in a single conversation, a friendship or trust that would ordinarily take years. It is genuine and remains after you stop tapping, though whether it survives what you do with it is up to you. |

}}

### Limits

- **It is not mind control.** Connection accelerates real relationships; it does not command. A creature you befriend is genuinely your friend, and a genuine friend can still refuse you, be hurt by you, and turn on you if you earn it.
- The **language and the sense of belonging fade** when you stop tapping. A bond you actually formed remains; the fluency that helped you form it does not.
- Connection is to people and places, not to facts. It will not tell you a secret, only make you the sort of person a secret gets told to.

### Interactions

- The Southern Scadrians used **unsealed** duraluminminds to speak with strangers across an ocean of unshared history. Such a mind must be filled unkeyed **from its first charge**, by someone storing their own Identity as they fill it, and it can then hand fluency and belonging to someone else.
- Storing Connection to vanish and tapping it to belong make a Connector a peerless infiltrator: unseen going in, and one of the family coming out.

{{note

| | |
|---|---|
| **Attribute** | Connection, the bonds between you and the world |
| **Storing** | Fade from notice (Stealth in the open, forgotten by witnesses); but no one will connect with you |
| **Tapping** | Build real rapport, then speak the local tongue and pass as a native, then forge lasting bonds in a conversation |
| **Limit** | Real relationships, not commands; fluency and belonging fade when you stop |

}}

\page

## God Metals of Feruchemy

*Not a quadrant. A category, and only one of them is understood.*

The God Metals are formed from the power of a Shard rather than mined. On the Feruchemical side only atium is known, and what it stores is **age**: fill it and grow old, tap it and grow young. It is not a bloodline chosen at character creation. It is the root of every story about someone who should have died a century ago and did not.

::::

## Other Metals (Feruchemy)

Beyond the sixteen ordinary metals lie the **God Metals**, formed from a Shard. As with Allomancy, these are **not bloodlines chosen at character creation**; they are rare, DM-placed materials. On the Feruchemical side, only one is understood.

- Atium stores **age**, more exactly **youth**. Its Feruchemical use is the one god-metal art that is well documented, and the root of the setting's most famous immortality.

The rest are blanks:

- **Lerasium's** Feruchemical properties are unknown.
- **Malatium** is an Allomantic alloy of atium and gold; it has no recorded Feruchemical use of its own.
- **Harmonium** and **Trellium** remain a mystery in Feruchemy as in everything else. See the God Metals.

### God-metal efficiency

A God Metal is condensed Investiture, and it does not fight its user the way lesser metals do. **Storing and tapping atium are instantaneous and lossless.** There is no shock to guard against, no side effect to survive, and none of the compression that makes an ordinary Ferring pay for a hard draw. What you put in, you take out. This is why a god-metal Compounder is so terrifying: the metal adds no friction of its own.

See the Ferring Bloodlines for the shared rules and the God Metals for the lore.

\page

## Atium (Feruchemical)

*The Lord Ruler aged a day into a bead each morning, and drew a day of youth back out each night, and so wore the same face for a thousand years.*

**Metal** Atium (god metal of Ruin) · **Attribute** Age · **Availability** DM-gated · **Capacity** 20 years per gram

Feruchemical atium stores **age**, or told the other way, **youth**. The name for one who does this alone is not recorded, for almost no one ever has. This is not a bloodline taken at character creation; see Other Metals, and the God Metals for the lore.

Because atium is a **God Metal**, storing and tapping it are **instant and lossless**: no shock, no side effect, no compression. A year banked is a year returned.

For the same reason, a **Feruchemist wields atium as a mastered metal from 1st level**, whatever quadrants they have taken. Pure Investiture has no alloy to learn your way around. What keeps atium out of reach is its rarity alone.

### Storing

While you fill an atiummind, you **age**. The years pour off you into the metal, and you grow visibly older: grey at the temples, lines at the eyes, a stiffness in the joints, banked as raw youth in the bead. You may age yourself by as many years as you dare in a moment, and it does you no harm beyond looking and feeling your new age.

### Tapping

While you tap an atiummind, you **reclaim banked youth**, growing physically younger by as many years as you draw, but **never younger than your true age**, the years you have actually lived.

- **Return to yourself.** Shed the years you stored, tapping banked youth to come back down toward your true age.
- **Undo stolen years.** Reverse **magical aging**, the decades drained by a ghost's touch, a wraith, or a curse, spending banked youth to set your body back toward its true age.
- **Appear older, never younger.** By storing, you can look and function as any age *above* your own, a disguise no paint can match. You can never appear younger than you truly are.

A single atiummind holds roughly **20 years per gram**, so a good bead can bank a whole human lifetime.

### Limits

**Atium moves age, and age alone.** It is not health and it is not vigor. It will not close a wound, cure a sickness, or restore a lost limb; those belong to gold. A younger body is still a body, and can still be killed like one.

**Time still runs one way.** Your body's age is your true age plus whatever youth you have banked away. Storing pushes it up; tapping brings it back down, at most to your true age, never below. And the clock never stops while you play with it. A woman of 20 who stores 60 years is 80 in body, and can tap straight back to 20, but if she lives five years at 80 before tapping, she returns not to 20 but to **25**. The banked youth is hers to reclaim; the five years she spent are simply spent. On its own, then, atium never lengthens a life; it only shuffles years within it. Adding years, rather than moving them, takes **Compounding**. Impressive, and of little practical use alone, exactly as with the Allomantic and other lesser-known god-metal arts.

### The immortal exception

Everything above is what atium does for a **Ferring**, and it is, as noted, of little practical use alone. Atium's fame belongs to the **Compounder**, which is a separate art with its own rules and its own section: see Compounding.

{{note

| | |
|---|---|
| **Attribute** | Age, a reserve measured in years; ~20 years per gram (a bead holds a lifetime) |
| **God-metal trait** | Storing and tapping are instant and lossless; no shock, no compression |
| **Storing** | Age yourself, banking youth |
| **Tapping** | Reclaim banked youth down to your true age (never below); undo magical aging; appear older |
| **Limit** | One-way clock: body age = true age + banked; time still passes, so it **cannot lengthen a life** alone. Adding years takes **Compounding** |

}}

\page

## Twinborn

A **Twinborn** is a character born with **one Allomantic power and one Feruchemical power**: a single Misting gift and a single Ferring gift, together in one person. They are rare, and they are versatile, holding a sliver of both halves of the Metallic Arts.

The two powers are **independent**. Your Allomantic metal and your Feruchemical metal are rolled or chosen separately, and they need not match. A Coinshot who is also a Windwhisperer, a Thug who is also a Bloodmaker, a Rioter who is also a Spinner: any pairing is possible.

### How a Twinborn works

A Twinborn simply **has both bloodlines** and uses each exactly as written on its own page. Your Allomancy follows the Misting rules (charges, flaring, tempo); your Feruchemy follows the Ferring rules (metalminds, rate and depth, compression). Nothing about having two powers changes how either one works, with one exception, below.

**Bloodline level.** Each of your two powers scales with your character level, just as a single bloodline does.

### Same metal: Compounding

If your Allomantic metal and your Feruchemical metal are **the same**, you are a potential **Compounder**, able to Allomantically burn your own charged metalmind for a massive, amplified burst of the stored attribute. This is the most powerful thing a Twinborn can do, and the rarest; its rules have their own page, Compounding. Because a random Twinborn lands on a matched pair only **1 time in 16**, most Twinborn are not Compounders.

### Resonance (optional, narrative)

In the lore, holding two Invested Arts produces a faint secondary effect called a **Resonance**, unique to each pairing. With 256 possible combinations and only a handful ever named, there is not enough known to give every pair a rule. This expansion **does not** mechanize Resonance. A DM who wants to may invent a small signature perk for a particular Twinborn, but none is required, and none is assumed.

### Building a Twinborn

At character creation, decide with your DM whether Twinborn are allowed (they are rarer than single Mistings and Ferrings, and Compounders rarer still). Then settle your two powers, by **choice** or by **the dice**.

#### Option A: Choose both

Pick any one **Allomantic** metal for your Misting power and any one **Feruchemical** metal for your Ferring power. Choosing the **same** metal makes you a Compounder, if your DM permits.

{{tableGroup

#### Option B: Roll each side

For each art, roll **1d4 for the quadrant**, then **1d4 for the metal** within it. Roll once for your Allomantic power and once for your Feruchemical power. God metals are never rolled; they are DM-placed.

**Allomantic power (your Misting):**

| 1d4 | Quadrant | Metal on 1 / 2 / 3 / 4 |
|---|---|---|
| 1 | Physical | Iron (Lurcher) / Steel (Coinshot) / Tin (Tineye) / Pewter (Thug) |
| 2 | Mental | Zinc (Rioter) / Brass (Soother) / Copper (Smoker) / Bronze (Seeker) |
| 3 | Enhancement | Chromium (Leecher) / Nicrosil (Nicroburst) / Aluminum Gnat / Duralumin Gnat |
| 4 | Temporal | Gold (Augur) / Electrum (Oracle) / Cadmium (Pulser) / Bendalloy (Slider) |

}}

**Feruchemical power (your Ferring):**

| 1d4 | Quadrant | Metal on 1 / 2 / 3 / 4 |
|---|---|---|
| 1 | Physical | Iron (Skimmer) / Steel (Steelrunner) / Tin (Windwhisperer) / Pewter (Brute) |
| 2 | Cognitive | Zinc (Sparker) / Brass (Firesoul) / Copper (Archivist) / Bronze (Sentry) |
| 3 | Hybrid | Cadmium (Gasper) / Bendalloy (Subsumer) / Gold (Bloodmaker) / Electrum (Pinnacle) |
| 4 | Spiritual | Chromium (Spinner) / Nicrosil (Soulbearer) / Aluminum (Trueself) / Duralumin (Connector) |

*If both rolls land on the same metal, you are a Compounder (DM permitting). Reroll if your table would rather avoid it.*

### Starting equipment

A Twinborn begins play with **both** a Misting's and a Ferring's starting gear: **1d6 grams** of their Allomantic metal as beads, and a **ring of 1d8 grams** of their Feruchemical metal.

\page

## Compounding

A **Compounder** is a Twinborn whose Allomantic and Feruchemical powers are the **same metal**. Where an ordinary Feruchemist can only ever draw back out what they put in, a Compounder cheats the ledger: they store an attribute Feruchemically, then **burn that charged metalmind Allomantically**, and Preservation's end-positive power pours out the stored attribute many times over.

This is the most powerful thing in the Metallic Arts short of a God Metal in the right hands, and it is how the Lord Ruler wore one face for a thousand years. It is also rare, and a DM is right to weigh whether to allow it. See Twinborn for how a same-metal pairing comes about, and the core rules for the underlying model.

{{tableGroup

### What Compounding does

When you burn a Feruchemically charged metalmind of your Compounding metal, you do **not** get its Allomantic power. There is no Steelpush, no coppercloud. Instead you draw out the **stored Feruchemical attribute, amplified**: you tap it as though you were drawing **many times** the charge you actually spend.

The multiplier grows with level, as your skill at the trick deepens.

| Level | 1–2 | 3–4 | 5–6 | 7–8 | 9–10 | 11–12 | 13–14 | 15–16 | 17–18 | 19–20 |
|---|---|---|---|---|---|---|---|---|---|---|
| **Compounding ×** | 2 | 3 | 4 | 5 | 6 | 7 | 9 | 10 | 12 | 15 |

}}

So a 5th-level gold Compounder who burns one hit point of stored health heals **four**. A 20th-level one heals fifteen. Whatever the metal, one unit spent becomes many drawn.

### The requirements

- **The same metal in both arts.** You must have that metal as a Misting power *and* as a Ferring power. Only a same-metal Twinborn can Compound.
- **The metalmind must be inside your body.** You can only Allomantically burn metal you have ingested or embedded, so a Compounder works from **swallowed beads** or **spikes under the skin**, never a ring worn on the hand. The mind must also be **your own or unsealed**; a locked mind you did not fill will not burn for you.
- **Stolen powers Compound too.** A matched pair taken by Hemalurgy Compounds exactly as a born pair does. This is precisely how the Steel Ministry built its Inquisitors: gold spikes to heal, pewter to be unbreakable, atium to stay young for a thousand years. A spiked Compounder pays the same metal costs as anyone, and carries the control risk of their spikes on top of it.

### The cost: metal burns away

Compounding spends metal exactly as Allomancy does. The charged metalmind is **consumed at its Allomantic rate** (its charges per gram and its tempo) as you burn it, so a bead of Compounding metal lasts only as long as the metal itself. When it is gone, it is gone, both the Investiture and the metal.

This is the true limit on a Compounder. Their power is not bounded by their body, as an ordinary Ferring's is, but by **how much of the right, perfectly-alloyed metal they can carry and keep swallowing.** A Compounder out of metal is only a Twinborn again.

### The endless well, and its bounds

The amplified attribute a Compounder draws out can itself be **stored again**, and then Compounded again, each cycle beginning with a larger reserve. In principle this is a bottomless well: exponential, unlimited, immortal.

In practice, three things hold it back.

- **Metal supply**, above: every cycle burns metal.
- **Each attribute's own ceiling.** Compounding multiplies the attribute, but the attribute's own limits still bite. A steel Compounder is still torn apart by air resistance; a pewter Compounder still cannot fit through a door; a brass Compounder can still cook themselves. The metal page's limits are not lifted, only fed.
- **Savanthood.** A body that comes to rely on Compounded power grows dependent on it, and a Compounder who cannot stop is on the road to a **Feruchemical savanthood** of their own art, and worse. Relentless Compounding of one metal fuses you with your *Feruchemy* the way heavy burning fuses an Allomancer with a metal: the effect deepens (a gold Compounder-savant outlasts even an ordinary gold Compounder), and the Dependency is real (the body that never stops mending cannot safely stop). Miles Dagouter tapped his healing constantly, and could not safely stop. See Feruchemical savants (through Compounding).

\page

{{wide

### What each metal becomes

Compounding turns modest Feruchemy into legend. Every pairing is listed here rather than scattered across the metal entries, because what a Compounder of a metal becomes is a fact about **Compounding**, not about the metal.

The attribute is the Feruchemical one; the Allomantic half of the pair only provides the burn.

| Metal | Attribute | What a Compounder becomes |
|---|---|---|
| **Iron** | Weight | Weight at will, from feather-light to immovable, far past what a Skimmer could bank |
| **Steel** | Speed | Speed without end, until the air itself stops you. Also lets a Twinborn **burn Allomantic metals faster**, since burning is a bodily process |
| **Tin** | Senses | A single sense sharpened past any natural limit, for as long as the metal lasts |
| **Pewter** | Strength | A nearly bottomless well of strength. Allomantic pewter can also be banked as Feruchemical pewter, making the cycle self-feeding |
| **Zinc** | Mental speed | Thought at a speed that makes conversation unbearable and calculation instant |
| **Brass** | Warmth | Heat drawn from Preservation itself. Survive what no store could hold, though making that much heat can cook even you |
| **Copper** | Memories | Perfect recall of far more than was ever filled in, the mind's archive multiplied |
| **Bronze** | Wakefulness | A limitless supply of wakefulness. **Need never sleep again** |
| **Cadmium** | Breath | **Need never breathe again**, drawing air from Preservation |
| **Bendalloy** | Nutrition | **Need never eat again**, drawing sustenance from Preservation |
| **Gold** | Health | Near-limitless healing. This is **Miles Hundred-Lives**, who took a blast to the face point-blank and walked away |
| **Electrum** | Determination | A will that cannot be turned aside by anything, for as long as you can pay |
| **Chromium** | Fortune | A truly extraordinary run of luck, though what that means is largely the table's to decide |
| **Nicrosil** | Investiture | The stored ability returned magnified far past your own ceiling. The most dangerous and least understood of all |
| **Aluminum** | Identity | A self so absolute that nothing can alter, read, or impersonate it |
| **Duralumin** | Connection | Connection enough to belong anywhere instantly, to anyone |
| **Atium** | Age | Draw out far more youth than you bank, and age backward faster than time carries you forward. True immortality. This is the **Lord Ruler**, and **Ironeyes** |

}}

**The four famous ones** are gold, atium, pewter, and steel, because those are the ones the histories record. The rest are no less possible; they are simply less often worth the metal.

{{imageMaskEdge6,--offset:10%,--rotation:0
  ![A gold Compounder](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/compounding-miles-hundredlives.jpg?v=bbebf734){height:100%}
}}

\page
{{partCover}}

# Part 2
## Species

{{imageMaskCorner26,--offsetX:-0%,--offsetY:-20%,--rotation:0
  ![Part 2 cover: a koloss](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/cover-species-koloss.jpg?v=c1c48f75){height:100%}
}}

\page

## Koloss-blooded

*Their grandparents were monsters made by a god, and then a better god unmade the making. What is left is a people: tall, blue-skinned, slow to anger, and very hard to put down.*

The **koloss-blooded** are what the koloss became after the Catacendre, when Harmony remade a doomed construct into a living race that could raise children instead of harvesting them. They live in tribes out in the Roughs, they keep their own laws, and they carry their ancestry in their skin, which runs from mottled granite to deep blue.

They are taller and heavier than humans, faster on their feet, and notoriously difficult to injure. They are also, contrary to a stereotype every one of them has heard, exactly as intelligent as anyone else.

### Koloss-blooded Traits

**Creature Type:** Humanoid
**Size:** Medium (usually 6 to 7 feet, and heavy for the height)
**Speed:** 35 feet

#### Powerful Build

You count as one size larger when determining your **carrying capacity** and the weight you can push, drag, or lift. You also have **advantage on checks you make to grapple or shove** a creature, and on checks and saving throws made to avoid being grappled or shoved yourself.

#### Koloss Hide

Your flesh is denser than a human's and lies over muscle that simply does not tear the way it should. When you take **bludgeoning or piercing damage from a nonmagical source**, reduce that damage by your **proficiency bonus**.

This is why the stories about koloss-blooded and gunfights are all true, and why nobody in the Roughs starts one lightly.

#### Koloss Vigor

You mend faster than a person has any right to. When you finish a **short rest**, you regain hit points equal to **your proficiency bonus + your Constitution modifier**, on top of any Hit Dice you spend. You also **stabilize automatically** at the start of your turn if you are dying, without needing a death saving throw.

#### Untiring

Your ancestors could live on ash and dirt and never felt the cold. You keep enough of that to be inconvenient to starve.

- You have **advantage on saving throws against gaining Exhaustion**.
- You can **eat anything organic** without harm, however spoiled, and you need only half the food a human does.
- You are comfortable in **extreme cold** and ignore its effects.

#### Growing Up Blue

You are the size you are and you stay there. The endless growth that killed your ancestors was a property of the **spikes**, not the blood, and Harmony took it out when he remade your people.

What you did inherit is the choice. At twelve, every koloss-blooded is offered four iron spikes and the chance to become a **true koloss**. Most refuse; those who accept leave childhood behind in a very literal sense. Those who refuse and then leave the tribe anyway, for a city or a road or a person, are where most adventuring koloss-blooded come from.

*You do not need to have taken the spikes, and almost certainly did not. See The Koloss Path if your character ever intends to.*

---

### The Koloss Path

> **Agree it at the table.** This is not a character option you take at 1st level. It is a thing that happens to a character during a campaign, it is irreversible, and it comes with an expiry date. Wanting your character to trade a lifespan for that strength is a legitimate choice, and nobody needs permission to make it. What is needed is that everyone at the table, the DM included, knows what they are agreeing to before anyone drives anything into anyone.

Four iron spikes, each charged with the strength of a person who died to provide it, driven into a living body with the right intent. The result is a **koloss**: enormous, tireless, and dying from the moment it is made.

The ritual is offered to every koloss-blooded at twelve, and the tribes will perform it for outsiders who ask, including humans. It works on anyone. The old koloss made new ones by force, from whoever was to hand.

\page
#### Becoming a Koloss

You gain four Hemalurgic spikes and the following changes. They replace nothing; they are added to what you already were.

- **Size and Strength.** Both **grow for the rest of your life**, and they grow together. Your starting size and strength, and everything they become, are on the Growth table below. You begin at roughly six feet and you do not stop.
- **Reach and weapons.** You can wield a weapon sized for a creature of your current size in one hand, and you may use whatever comes to hand as an improvised weapon at no penalty. Koloss traditionally carry crude oversized blades and swing them by inertia alone.
- **Tireless.** You are **immune to Exhaustion**, and you do not need to sleep, though you rest anyway out of habit.
- **Dulled to pain.** You have **advantage on saving throws against effects that would incapacitate you through pain**, and you can act normally while at 1 hit point without any sign of distress.
- **Dulled in mind.** The spikes take something. You have **disadvantage on Intelligence and Charisma checks** made to do anything subtle: recall detail, reason abstractly, deceive, or persuade. You keep your speech, your memories, and your reasoning; you simply find all of them harder to reach than you used to.
- **You keep what you had.** A Misting who becomes a koloss **keeps their bloodline**, a Mistborn keeps theirs, and a Twinborn keeps both halves, though many koloss forget how to use what they still have. If those two halves happen to be **gold**, everything below changes; see The One Exception.
- **You cannot take more spikes.** Four is the whole of it. A fifth will not take, and the four you have cannot be exchanged or added to.

#### Four Spikes

You bear **four Hemalurgic spikes**, which puts you at the **4 to 6** tier of the Control Risk table. That is not a small thing:

- You have **disadvantage on saving throws against emotional Allomancy**.
- A Shard, or a coordinated group of Soothers and Rioters, **can seize control of you**, and once seized that control **persists without further effort** until something breaks it. This is exactly how the Lord Ruler ran his armies, and how Ruin ran them after him.
- Your Wisdom saving throws against such control are made with **disadvantage**.

A koloss who is not being steered by someone is a koloss whose spikes nobody has bothered to reach for yet.

{{tableGroup

#### Growth: the body outruns the skin

**Everything about you grows except your skin.** Your muscles thicken, your bones lengthen and thicken with them, your heart and lungs strain to keep up. Only the skin stays the size it was on the day you were spiked, and that single failure is what eventually kills you.

Growth is measured in **years, not levels**. A campaign spanning a season will barely move a koloss along this table; one spanning a decade will change what the character fundamentally is.

| Years since the spiking | Height | Size | Strength | The skin |
|---|---|---|---|---|
| **0 to 5** | About 6 feet | Medium | Advantage on Strength checks and saves. Unarmed strikes deal **1d8** | Hangs loose and baggy. You look wrong and you know it |
| **5 to 12** | 7 to 8 feet | **Large** | As above, and unarmed strikes deal **1d10**. Count as one size larger for carrying | Drawn tight at last. You look, briefly, magnificent |
| **12 to 20** | 9 to 10 feet | Large | Unarmed strikes deal **2d6**. Your **Strength score becomes 22** if it was lower. You deal **double damage to objects and structures** | Splitting. You wrap the tears in leather and keep going |
| **20 to 25** | 11 to 12 feet | Large (and unmistakable) | Unarmed strikes deal **2d8**. Your **Strength score becomes 25** if it was lower. You count as a **siege weapon** against objects and structures | Bare muscle over most of you. Your heart labors. Every year is borrowed |
| **Beyond 25** | Over 12 feet | Large | Unarmed strikes deal **2d8** | Your heart and lungs can no longer supply your body, and you begin to die of it, as any person does who reaches the end of their life |

}}

\page
**What that late strength means in practice.** A koloss past its second decade is not a large warrior; it is a piece of siege equipment that can hold a conversation. It shatters a city gate the way a battering ram does, walks through a stone wall rather than around it, and lifts what a team of horses would strain at. Anything it hits that is not alive should generally just break.

**Roughly twenty-five years, and then you begin to die.** That is the span of a koloss, measured from the ritual rather than from birth, so one who took the spikes at twelve is old at thirty-five and enormous. **Leather wraps** over split skin, changed and tended, prevent the slow bleeding that would otherwise kill you years early, and every koloss who intends to reach old age learns this. Nothing else helps. There is no treatment, no regimen, and no healer who can extend a koloss past its span.

Whatever you were when you were spiked is what you have to work with for the rest of your life, because you cannot take a fifth spike to fix anything.

#### The One Exception

There is exactly one way a koloss lives past its span, and it is not a treatment. It is a matter of who you were before.

**A gold Compounder who becomes a koloss keeps Compounding.** Someone who already possessed both Allomantic and Feruchemical gold, a natural Twinborn of that metal, carries that ability through the ritual as any Allomancer carries theirs. From then on they heal themselves as fast as their own body tears, indefinitely, by their own power and nobody else's. Miles Hundred-Lives is the obvious candidate, and the reason the thought is terrifying.

Such a koloss keeps growing, past twelve feet and onward, held together by continuous self-healing. **The ceiling is twenty feet.** Growth stops there and never resumes, and nothing has exceeded it. What stands at twenty feet is no longer a person-shaped problem; it is a walking siege that the world organizes itself around removing.

#### Playing a Koloss

If a player takes this path, they have chosen a tragedy on purpose, and the table should treat it as one. The character is enormously strong, effectively unkillable by ordinary means, and on a timer that no amount of adventuring will reset. They are also, in a way the party will feel, **steerable** by anything that knows how to reach four spikes.

Handled well it is one of the best character arcs this setting offers. Handled carelessly it is a way for one player to become an NPC.

{{imageMaskEdge6,--offset:10%,--rotation:270
  ![A koloss-blooded human](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/species-koloss-blooded.jpg?v=3a57da68){height:100%}
}}

{{imgph imgphWide,style=min-height:19em
<!--h:34-->
**[ART: koloss-growth]** *Growth silhouettes to scale, six feet through twenty, showing the five bands of a koloss life with heights labelled.*

**WIDE** not supplied | ratio 2.50:1
}}

\page

## Kandra

*A kandra has no face of their own. They have a set of bones they are wearing at the moment, a memory of every body they have ever worn, and two spikes of metal somewhere inside them that are the only part they cannot replace.*

The **kandra** are Mistwraiths given a mind. A pair of Hemalurgic spikes, called **Blessings**, were driven into a mindless gelatinous thing and made it a person. That was the Lord Ruler's work, and the making of new ones is lost. Every kandra alive was made long ago, and most are older than the nations they walk in.

A kandra digests a corpse and reassembles themselves around its bones, becoming that creature exactly. They have served as spies, as servants under Contract, and as the quiet keepers of secrets. They are very patient, having lived for so many centuries.

### What a Kandra cannot be

Kandra are not born and have no bloodline to inherit.

- You **cannot take a Misting or Ferring bloodline**, and you **cannot be a Feruchemist**. The Metallic Arts do not run in a body that was assembled rather than conceived.
- You **can** become a **Mistborn** by burning a bead of lerasium, the one road open to anyone.

Every other class is open to you.

### Kandra Traits

**Creature Type:** Ooze
**Size:** Small while boneless, otherwise the size of the body you wear (Medium or Small at 1st level)
**Speed:** 15 feet while boneless, otherwise the speed of the body you wear

#### Boneless Form

Your true shape is a translucent mass of flesh, and it is the state you return to when you have nothing to wear. While boneless you are a **Small** Ooze with a speed of **15 feet**, you can **squeeze through any opening a fist could pass**, and you can neither wear armor nor use a weapon or a tool that requires a grip. Your unarmored AC is **10 + your Dexterity modifier**. You can speak only if you shape a throat, which takes an action.

You may abandon your bones and revert to this form deliberately as an action. Doing so leaves the bones behind. In this form you can fit through a gap at least as wide as your Blessings.

{{tableGroup

#### Digest and Mimic

Given a corpse with an intact skeleton, you can consume it and rebuild yourself as a perfect copy. This is careful work, not a combat trick.

**The time it takes** depends on the body's size and how much hair, fur, feathers, or scales it carries, since each must be placed individually.

| Size | Bare skin | Some hair | Moderate fur | Fully covered |
|---|---|---|---|---|
| **Small** | 10 minutes | 1 hour | 3 hours | 5 hours |
| **Medium** | 1 hour | 2 hours | 4 hours | 6 hours |
| **Large** | 3 hours | 4 hours | 6 hours | 8 hours |

}}

A human takes about an hour, which covers the hair of the head and face. **A body you have worn before takes half as long.** You may skip the hair entirely and finish in the bare-skin time, but you lose the benefits of that covering. You can mimic any creature that can bear your spikes, though non-humanoid creatures take twice as long.

**What you gain.** You become the creature in every physical respect:

- Its **size**, its **speed**, and all its **movement modes** (climb, swim, burrow, fly).
- Its **Strength and Dexterity scores**, replacing your own.
- Its **natural senses**, including darkvision, blindsight, keen smell, and the like.
- Its **natural weapons**, natural armor, and physical traits such as holding its breath, and its exact appearance and voice.

**What you do not gain.** You keep your own **Constitution, Intelligence, Wisdom, and Charisma**, your hit points, your class features, and all your proficiencies. You gain **no magical or supernatural ability** of the creature: no spellcasting, no innate magic resistance, and no Metallic Art. You are wearing a body, not a soul.

**Organic abilities.** If an ability comes from a *physical organ* rather than from magic, you can mimic it by reproducing the organ exactly. A breath weapon produced by a gland, a spitter's venom, an electric organ, or a squid's ink are all fair game. Anything the creature does by will alone does not. When it is unclear, the question to ask is whether a surgeon could find the thing that does it.

**What you can wear.** At 1st level you can copy **Small and Medium humanoids**. This widens as you grow (see Growing Older). You can wear the body of any creature whose frame can carry your spikes.

**Function Over Form.** Everything above concerns an **exact replica**, which is the hard art and the one that takes practice. Simply having *a* working body is not hard, and every kandra can do it from their first day. Given any usable set of bones, matched or not, you can assemble a functioning creature in the bare-skin time on the table. It will move, fight, and carry you perfectly well.

\page
{{tableGroup

#### Your Skeleton

Bones are one of the things a kandra cannot form from flesh. You must take them from a body or have them crafted, and what they are made of determines how durable you are.

**Unarmored Defense.** While wearing a skeleton and not wearing armor, your AC equals your **skeleton's AC**. You may wear armor instead and use its AC as normal.

**True Bodies.** Rather than a digested skeleton, a kandra may wear a crafted set of false bones, and most prefer to while not on jobs. In the Homeland they wear their skin translucent to show off their true body.

| Skeleton | AC | Notes |
| ----------------------------------------- | --- | ------------------------------------------------------------------------------------------------------------------------------- |
| Ordinary bone | 14 | Whatever you last digested. Free |
| Wood | 14 | Speed +5 ft. You float, and can swim without extra effort |
| Crystal | 15 | Beautiful and prized. Shatters under a hard blow (disadvantage on the save against breaking, below) |
| Stone | 15 | You weigh about half again as much, with advantage against being grappled or knocked prone |
| Copper, brass, or bronze | 16 | Heavy, and worth stealing |
| Iron or steel | 17 | You may build in **hidden compartments** and **retractable blades** (a d6 finesse natural weapon) |
| Aluminum | 15 | Cannot be affected by Allomantic Pushes or Pulls, and cannot be sensed as metal |
| Exotic (mithral, adamantine, or stranger) | 18+ | Legendary work, entirely the DM's to place |

}}

**Heavy bones do not slow you.** A kandra simply grows the extra muscle needed to carry them. What a heavy skeleton actually costs you is **upkeep**: more muscle needs more meat, and a stone or steel kandra eats noticeably more than a bone one. It also makes you heavy, which matters for swimming, climbing, thin ice, and rotted floors.

Anything above ordinary bone must be **commissioned from a kandra artisan or crafted yourself**, and metal skeletons in particular are the price of a suit of comparable armor. A DM should treat a fine skeleton as treasure or fine craftsmanship, not as simple shopping.

#### Broken Bones

You have no organ that a blade can find, but your bones can be shattered, and you cannot mend them.

- When a creature scores a **critical hit** against you, or deals damage in a single hit equal to or greater than **your level + your proficiency bonus**, it rolls one additional attack roll against your **skeleton's AC**. On a hit, **a bone breaks**.
- Each broken bone reduces your **speed by 2 feet** and your **skeleton's AC by 1**.
- **Broken bones do not heal** by rest, by any power that mends flesh, or by any healing worked on you while they are inside you. A broken bone **taken out of your body** can however be repaired like any other object, including with a *mending* cantrip. They can also be reinforced with normal bracing techniques.
- **Replacing a bone** takes time according to what it is. A small bone (a finger, a rib, a tooth) is the work of a **moment**. A **structural** bone (a skull, a spine, a long bone of the arm or leg) takes about **10 minutes** for a young kandra, and less as you grow practiced.
- Only **structural** bones are tracked. Small bones break constantly and cost you nothing worth writing down.
- If **every structural bone you carry is broken or destroyed**, your frame gives out and you collapse into your Boneless Form. You are **not** Incapacitated. You can still see, speak, think, and act, but you are reduced to a boneless crawl at **15 feet**, you cannot use weapons, armor, or anything needing a grip, and you are horribly exposed until you reinforce or replace some part of your skeleton.

*Truly destroying a kandra takes more than this. You must burn or dissolve away all of their flesh, or remove both spikes and destroy them.*

#### Unnatural Body

Your organs are wherever you decided to put them, and none of them are where anyone would look.

- You are **immune to the effects of critical hits other than the Broken Bones rule above**; there is no vital spot to find, and a blade through where a heart should be finds only flesh.
- You **cannot be knocked unconscious by physical shock or pain**. You can turn your nerves off entirely, giving you **advantage on saving throws against effects that would incapacitate you through pain**.
- You **do not age** and cannot be aged magically. You need not sleep, but you must **eat meat**, since you are constantly renewing your own flesh. Any meat serves, not only corpses, and most kandra prefer it **well aged**, which is easier to digest. Starvation is one of the few things that can kill you.
- You are **vulnerable to acid and fire damage**, which destroy flesh faster than you can reshape it.

**Falling apart, not dying.** Ordinary wounds do not kill a kandra; they take you apart. When you drop to 0 hit points you still make death saving throws, but for you they are **checks against coming apart entirely**, not against dying.

\page

- On **three failures**, you do not die. Your flesh loses cohesion and you collapse into an inert, senseless heap: unconscious, helpless, and unable to be roused. You remain in that state until someone tends to you, and any healing at all restores you to 1 hit point and full awareness.
- **Fire and acid are the exception.** If the damage that dropped you to 0 was fire or acid, or if fire or acid is applied to you while you are down, those saves are exactly what they are for anyone else, and three failures kill you for good.
- While you lie inert you can still be **destroyed deliberately**, by burning your flesh away or by finding and destroying both of your spikes. A thorough enemy knows this. A careless one leaves you to reassemble.

#### Sculpt Flesh

You can reshape your own flesh at will, though never your bones.

- As an action you may make **minor changes to your appearance**: alter your features, add or shed wrinkles and scars, change your skin's color, shed your hair, or make your skin **translucent**. You cannot imitate a specific person this way; that requires their bones.
- You may **split your skin and seal an object inside your body**, carrying anything up to the size of a dagger. An object hidden this way cannot be found by search, and **metal concealed in your flesh cannot be sensed or targeted by Allomancy**, which has made kandra the preferred couriers for things nobody should be carrying.

#### Your Blessing

Choose one of the four Blessings when you make your character. It is the pair of spikes that made you a person, and it never changes.

**Blessing of Awareness** (a pair of tin spikes). Your senses are heightened as though you burned tin.
- You gain **Darkvision** to a range of 60 feet, or extend existing darkvision by 60 feet.
- You have **advantage on Wisdom (Perception) checks**, and you notice a hidden creature within 15 feet without needing to search.
- Sudden brightness or a great noise overwhelms you: you have **disadvantage on saving throws against effects that Blind or Deafen**.

**Blessing of Potency** (a pair of iron spikes). Your limbs are stronger than the body you wear should allow, though without a Thug's endless energy.
- You have **advantage on Strength checks and Strength saving throws**.
- Your **speed increases by 5 feet**, and you count as **one size larger** for carrying capacity, pushing, dragging, and lifting.
- You have **advantage on death saving throws**.

**Blessing of Presence** (a pair of copper spikes). Your mind is clear in a way that flesh cannot cloud.
- You have **perfect recall** of anything you have seen or heard, with no time limit.
- You have **advantage on Constitution saving throws to maintain concentration**, and on saving throws against being **Frightened** or driven mad.
- Your spikes trouble you less than most. You have **advantage on saving throws against being controlled**, including by a Shard (see below).

**Blessing of Stability** (a pair of zinc spikes). Your feelings are your own and cannot be reached. Rarely given, and prized by those who have it.
- You are **immune to emotional Allomancy**, whether a Rioter's or a Soother's.
- You have **advantage on saving throws against being Charmed**, and you cannot be compelled to act against your own nature by magic.

#### The Two Spikes

You bear **two Hemalurgic spikes**, and they are your mind. This is not free.

- You count as bearing **two spikes** on the Control Risk track: you have **disadvantage on saving throws against emotional Allomancy**, and a **Shard or comparable power may attempt to influence you**. The **Blessing of Presence** grants advantage against that influence, and the **Blessing of Stability** removes the emotional-Allomancy weakness entirely. Most kandra choose one of those two for exactly this reason.
- **Losing one spike** leaves you sane but fraying. You keep your mind, but your memories develop holes that widen the longer it is gone, and the DM may rule that you no longer remember something you relied upon. Oddly, with only one spike **no god can touch you at all**.
- **Losing both spikes** ends you as a person. You revert to a mindless Mistwraith and are no longer playable until they are recovered and returned. Destroy them, and there is nothing left to bring back.

Additional spikes you take through Hemalurgy stack on top of these two, moving you up the Control Risk table. A kandra who arms themselves with stolen powers becomes very dangerous and very easy to steer.

\page
{{tableGroup

### Growing Older

Kandra improve at their art with practice, and yours does so as you level.

| Level | You gain |
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1st** | Copy **Small and Medium humanoids**. Digestion takes the time on the table. |
| **5th** | Halve all digestion times. You may **reinforce a broken bone** with a lattice of ligament, suppressing its penalties for a number of hours equal to your level. This takes **1 minute** at 5th level, an **action** at 10th, and a **bonus action** at 15th, as the trick becomes second nature. |
| **10th** | Copy **non-humanoid** creatures with an internal skeleton, and **Large** bodies. A body built from **mismatched bones** can now be made convincing, passing as a real creature of its kind rather than obviously being a construction. |
| **15th** | Work from **decayed or partial remains**, reconstructing an **exact** likeness by inference. A body you have worn before takes **10 minutes**. |
| **20th** | Copy a creature from **its bones alone**, having never seen it alive, and change into a body you have mastered as a **single action**. |

}}

\column

### Playing a Kandra

- **You are wearing someone.** Every body you have came off a corpse. Some tables will want that examined and some will not; agree in advance.
- **Your bones are your gear.** Losing them is the kandra equivalent of losing your armor and your legs at once, and replacing them is a scene rather than a purchase. Keep a spare skeleton if you can afford one.
- **You remember.** Kandra live for centuries and most have served Contracts under masters long dead. Whatever your character has forgotten, they forgot because a spike was out.

\page
{{partCover}}

# Part 3
## Backgrounds

{{imageMaskCorner25,--offsetX:-0%,--offsetY:-30%,--rotation:2
  ![Part 3 cover: a hazekiller](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/cover-backgrounds-hazekiller.png?v=a0d4fda8){height:100%}
}}

\page
## Backgrounds and Origin Feats

Five backgrounds for characters who grew up around the Metallic Arts. They describe trades and lives that exist wherever people burn metal, so they drop into an ordinary D&D world alongside Acolyte, Criminal, and Soldier without asking the DM to import an empire.

Each follows the 2024 shape: three ability scores (assign **+2/+1** or **+1/+1/+1**), one **Origin feat**, two skills, one tool, and either a themed kit or **50 GP**.

> Backgrounds do **not** grant a bloodline. Being a Misting, a Ferring, or a Twinborn is chosen separately (see Misting Bloodlines), and any background can pair with any of them, or with none.

---

### Alloyer

*A false alloy is a dead alloy. Ninety-one percent tin and nine percent lead is pewter; ninety and ten is a lump of metal that will kill an Allomancer who trusts it. You are one of the people who knows the difference, and can prove it.*

You were raised in a foundry, an assay office, or the back room of a shop that sold vials to people who did not explain what they wanted them for. Allomancy runs on exactness, and exactness is a trade.

**Ability Scores:** Intelligence, Dexterity, Constitution
**Origin Feat:** Alloyer
**Skill Proficiencies:** Arcana and Investigation
**Tool Proficiency:** Smith's tools
**Equipment:** *Choose A or B:* (A) Smith's tools, a set of assay scales and weights, sample beads of six pure metals, a ledger of alloy ratios, traveler's clothes, and 15 GP; or (B) 50 GP.

---

### Hazekiller

*Anyone can kill a man. Killing a man who can throw you across a courtyard by the buckles on your coat takes training, and the first lesson is what you stop wearing.*

You were trained, formally or otherwise, to fight people with powers you do not have. Guards, house security, bounty hunters, and the occasional very determined widow all learn the same handful of tricks: carry no metal, close the distance, and go for the vials.

**Ability Scores:** Strength, Dexterity, Wisdom
**Origin Feat:** Hazekiller
**Skill Proficiencies:** Athletics and Perception
**Tool Proficiency:** One gaming set of your choice
**Equipment:** *Choose A or B:* (A) A dueling cane, an aluminum-lined cap, 50 feet of rope, a horn lantern, common clothes with wooden fastenings, and 10 GP; or (B) 50 GP.

*Note the absence of manacles. A Hazekiller binds a prisoner with rope, because iron manacles are a gift to anyone who can Push on them.*

*An **aluminum-lined cap** shields the wearer's mind from emotional Allomancy, as aluminum always has. It is the single most valuable thing most Hazekillers own.*

---

### Crewmember

*Every job needs a smoker, a lurcher, a tineye on the roof, and somebody who knows which guard drinks. You were usually the last one.*

You worked a crew: thieves, rebels, smugglers, or something with a nicer name and the same working hours. Crews are where people with unusual powers meet people who can plan, and you learned to be useful to both.

**Ability Scores:** Dexterity, Charisma, Intelligence
**Origin Feat:** Skilled
**Skill Proficiencies:** Deception and Stealth
**Tool Proficiency:** Thieves' tools
**Equipment:** *Choose A or B:* (A) Thieves' tools, a dark hooded cloak, a crowbar, a set of forged papers, ten feet of knotted cord, and 15 GP; or (B) 50 GP.

---

### Metal Smuggler

*Nobody stops a man carrying tin. Everybody stops a man carrying aluminum. The trade is in knowing which is which, and in the case with the false bottom.*

Where the Metallic Arts matter, somebody controls the metals, and somebody else moves them anyway. You know routes, prices, inspectors, and exactly how much a sealed vial is worth three towns over.

**Ability Scores:** Dexterity, Charisma, Constitution
**Origin Feat:** Lucky
**Skill Proficiencies:** Deception and Sleight of Hand
**Tool Proficiency:** Forgery kit
**Equipment:** *Choose A or B:* (A) A forgery kit, a case with a false bottom, a pouch of assorted metal beads worth 10 GP, a merchant's seal that is not yours, traveler's clothes, and 10 GP; or (B) 50 GP.

---

### Ashworker

*Sweeping, hauling, digging, breathing it. Whatever fell out of the sky or came up out of the ground, somebody had to move it, and you were somebody.*

You did the work nobody writes down: ash, slag, tailings, sewers, mine faces, foundry floors. It made you hard to tire, hard to disgust, and unimpressed by most of what frightens other people.

**Ability Scores:** Constitution, Strength, Wisdom
**Origin Feat:** Tough
**Skill Proficiencies:** Athletics and Survival
**Tool Proficiency:** Mason's tools
**Equipment:** *Choose A or B:* (A) A shovel, a breathing scarf, a lantern, heavy work clothes, a whetstone, and 10 GP; or (B) 50 GP.

---

\page

## Origin Feats

Two new Origin feats. Either may be taken by any background that grants an Origin feat, at the DM's discretion, not only the ones above.

### Alloyer (Origin Feat)

*Prerequisite: none*

You understand metal as a recipe rather than a substance.

- **Assayer's Eye.** By examining a sample for 1 minute, you learn a metal's exact composition, and you know immediately whether it is **pure enough to be burned**. You cannot be sold a false alloy, and you can tell at a glance whether a vial someone else is carrying will work.
- **Perfect Alloy.** Given a forge, raw materials, and 8 hours of work, you can produce **Allomantically pure** alloys of any metal whose ratio you know. You may also refine impure metal into usable form, recovering roughly half of it.
- **Trade Knowledge.** You gain proficiency with **smith's tools** and **alchemist's supplies**, and you pay **half price** for metals bought in bulk, because you know who is watering the stock.

### Hazekiller (Origin Feat)

*Prerequisite: none*

You were taught how people with metal in their stomachs move, and what to do about it.

- **Trained Eye.** You have **advantage on Wisdom (Perception) and Intelligence (Investigation) checks** to work out whether a creature is using a Metallic Art and which metal it is, judging from stance, focus, and what they are looking at. This is deduction, not sense: a coppercloud does nothing to stop it, and neither does anything else, but a creature doing nothing tells you nothing.
- **Nothing to Grab.** The first lesson is not a stance, it is an inventory. You have trained yourself out of ever wearing or carrying metal, and your kit is built accordingly: wood, leather, bone, horn, ceramic, and aluminum where nothing else will do. You can outfit yourself this way at no additional cost, and you notice immediately when you are carrying metal you did not intend to.

 Because there is nothing on you to take hold of, **an Allomancer cannot Push or Pull you by your gear at all**. They can still Push metal that happens to be near you, and if you are ever carrying metal (a looted blade, a coin someone slipped into your coat) you are as vulnerable as anyone until you get rid of it, which you can do as a **reaction**.
- **Cane Work.** You gain proficiency with the **dueling cane**, a wooden weapon dealing **1d6 bludgeoning** damage with the **finesse** property. Hazekillers favor them for the obvious reason: there is no metal in them to be turned against you.

---

\page
{{partCover}}

# Part 4
## Classes

{{imageMaskCorner26,--offsetX:-0%,--offsetY:-30%,--rotation:0
  ![Part 4 cover: a Mistborn against an army of Inquisitors](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/cover-classes-storms-that-shatter.jpg?v=9622a887){height:100%}
}}

\page

## Mistborn

*A Mistborn burns all sixteen metals. Where a Misting is a single note, a Mistborn is the whole chord: pushing off a coin to sail over a rooftop, flaring pewter to land and run, soothing the guards to sleep as they pass.*

A **Mistborn** can burn **every** Allomantic metal, not just one. They are vanishingly rare, the product of a lerasium line or a lerasium bead, and they are among the most dangerous individuals on Scadrial. This class turns that breadth into a full character path.

> **How Mistborn Allomancy works.** A Mistborn uses the same metal economy as a Misting: charges, tempos, flaring, the force tables, and Constitution as the Allomantic ability. Each metal's actual effect is on its its own entry.

### Two hard restrictions

Being Mistborn is a matter of birth and soul, not training, so it sits differently from an ordinary class.

- **Mistborn must be your class at 1st level, and you cannot multiclass *into* it later** by ordinary means. You are born Mistborn or you are not.
- **The one exception is lerasium.** Burning a bead of lerasium can make a character Mistborn mid-life, and *only* then may Mistborn be taken as a later class, at the DM's discretion. This is a legendary, campaign-shaping event, not a normal level-up.

(A Mistborn may freely multiclass *out* into other classes; the restriction is only on entering.)

### Core Mistborn Traits

**Hit Point Die:** D8 per Mistborn level
**Saving Throw Proficiencies:** Constitution and Charisma
**Skill Proficiencies:** Choose 2: Acrobatics, Athletics, Deception, Insight, Intimidation, Perception, Sleight of Hand, Stealth
**Weapon Proficiencies:** Simple weapons, plus daggers, dueling canes, and hand crossbows
**Armor Training:** Light armor
**Allomantic Ability:** Constitution (save DC 8 + PB + Con; attack bonus PB + Con)

*A Mistborn who wears much metal makes themselves a target for enemy Coinshots and Lurchers; most wear little more than a cloak.*

**Starting Equipment:** Choose A or B:
(A) a **mistcloak**, obsidian daggers, four vials of metal flakes (of the metals you can master), a pouch of beads of the other non-God metals, dueling cane, explorer's pack, and 10 GP; or (B) 75 GP.

### The Mistborn (level table)

{{classTable,frame,decoration,wide

| Level | PB | Features | Burn Budget | Metals Mastered |
|---|---|---|---|---|
| 1 | +2 | Allomancy, Metallic Mastery (1st quadrant), Mistcloak | 4 | 4 |
| 2 | +2 | Allomantic Instinct | 4 | 4 |
| 3 | +2 | Quadrant Mastery | 6 | 4 |
| 4 | +2 | Ability Score Improvement | 6 | 4 |
| 5 | +3 | Metallic Mastery (2nd quadrant), Rapid Burning | 9 | 8 |
| 6 | +3 | Quadrant Mastery | 9 | 8 |
| 7 | +3 | Improved Flaring | 12 | 8 |
| 8 | +3 | Ability Score Improvement | 12 | 8 |
| 9 | +4 | Metallic Mastery (3rd quadrant) | 15 | 12 |
| 10 | +4 | Quadrant Mastery | 15 | 12 |
| 11 | +4 | Emergency Metals | 18 | 12 |
| 12 | +4 | Ability Score Improvement | 18 | 12 |
| 13 | +5 | Metallic Mastery (4th quadrant) | 22 | 16 |
| 14 | +5 | Quadrant Mastery | 22 | 16 |
| 15 | +5 | Practiced Duralumin | 25 | 16 |
| 16 | +5 | Ability Score Improvement | 25 | 16 |
| 17 | +6 | Allomantic Savant | 28 | 16 |
| 18 | +6 | Deepening Mastery | 28 | 16 |
| 19 | +6 | Epic Boon | 32 | 16 |
| 20 | +6 | Mistborn Ascendant | 32 | 16 |

}}

\page
### Class Features

#### Allomancy (1st level)

You can burn **all sixteen** Allomantic metals, using the metal economy of the Misting Bloodlines: you ingest metal, feel your reserve, and burn charges at each metal's tempo, flaring for more.

- **Per-metal flare cap = your Mistborn level**, exactly as a Misting of that level. You are never a *better* burner of a single metal than a specialist Misting; your edge is breadth, not depth.
- **Burn Budget (breadth).** The **total** charges you may spend across **all** metals in a single tempo unit is given in the level table (4 at 1st, rising to 32 at 20th). This is what lets you run several metals at once, an ordinary Misting's impossible dream.
- **Snapping.** You have already Snapped. Your Allomancy is always available so long as you have metal.

You can attempt to burn any metal you have, but you burn **unmastered** metals poorly (see Metallic Mastery). You can burn the **God Metals** (the God Metals) at **full efficiency from 1st level**; they are held in check by their extreme rarity, not by any limit of yours.

#### Metallic Mastery (1st, 5th, 9th, 13th levels)

The sixteen metals fall into four quadrants. At 1st level, choose one quadrant to **master**. Your first quadrant must be **Physical, Mental, or Temporal**; these three shape a Mistborn's craft and grant a Quadrant Mastery. (The **Enhancement** metals, the Gnat and Leech metals that act only upon other metals, have no path of their own; there is no way to make an aluminum or duralumin burn subtler than it already is. You will master Enhancement as one of your later quadrants.) You gain three more masteries at 5th, 9th, and 13th level, choosing a new quadrant each time, until at 13th level you have mastered all four and wield every metal at full skill.

- A **mastered** metal is burned exactly as its Misting page describes: full charges, full magnitude, flare cap equal to your level.
- An **unmastered** metal gives you only **half** the charges from a given amount of metal and **half** the magnitude of its effect, and you may not flare it above **half your level**. You can use it in a pinch; you cannot rely on it.

#### Mistcloak (1st level)

You own a **mistcloak**, a garment of countless tasseled strips worn by Mistborn since the Final Empire. While you wear it and are burning at least one metal, you have **advantage on Dexterity (Stealth) checks** made in mist, fog, dim light, or darkness, and you may take the Hide action as a bonus action. A lost mistcloak can be remade by a skilled tailor over a few days.

#### Allomantic Instinct (2nd level)

Burning metal sharpens you. While you are burning any metal, you have **advantage on initiative**, and you cannot be surprised unless you are Incapacitated.

#### Quadrant Mastery (3rd, 6th, 10th, 14th levels)

A Mistborn eventually masters every metal, but the quadrant you master **first** shapes you most deeply, and your soul, closer to Preservation than any Misting's, learns to make its metals sing together in ways no specialist ever could. Your **starting quadrant** (Physical, Mental, or Temporal, chosen at 1st level) grants you a **Mastery** feature at 3rd level, and again at 6th, 10th, and 14th, listed under Quadrant Masteries below. You do not choose a separate subclass; your first quadrant *is* your path.

**A Mastery is never free.** Every Mastery refines how you *burn* one or more metals. To gain its benefit you must be **burning the relevant metal and spending its charges** exactly as its Misting page requires; a Mastery sharpens or combines your Allomancy, but it never grants an effect without the burn behind it. Each quadrant's **14th-level** Mastery is the same in kind: you become a **savant of that quadrant's four metals**. Being a savant is the only way to burn a metal past its flare cap, so this is what unlocks the quadrant's most extreme feats, bounded now only by your Burn Budget and the metal you carry. It also brings a savant's **Dependency**: while you are a savant of one of these metals but not burning it, you suffer withdrawal until you resume (see Savants).

#### Rapid Burning (5th level)

Your reflexes and your reserves have grown enough to act on several metals at once. Once on each of your turns, when you take the Attack action or use a metal's effect that requires an action, you may use a **second** metal's action-cost effect as a **bonus action**.

#### Improved Flaring (7th level)

When you flare a metal, you may spend **one charge fewer** than normal for the same effect (minimum one), letting your reserves stretch further under hard use.

#### Emergency Metals (11th level)

You are never quite caught empty. You can retrieve and swallow a bead or vial of metal, or bite down on a stored one, as a **free action once on each of your turns**, even while falling, grappled, restrained, or otherwise hard-pressed, so long as the metal is on your person. A Mistborn who has just hurled themselves off a tower with a great Push can down a fresh vial before they land.

\page
#### Practiced Duralumin (15th level)

Your handling of the enhancement metals is second nature. You may burn duralumin or nicrosil as a **bonus action or a reaction**, rather than only as an action, letting you time a detonation to the exact moment it is needed.

#### Allomantic Savant (17th level)

A lifetime of burning has etched the metals into your soul, faster than any year of use could. Choose **two** metals you have mastered and are not already a savant of; you become a full savant of them, gaining a doubled flare cap and doubled efficiency with each. Like every savant, you also take on **the Dependency** for those metals: while you are a savant of a metal but not burning it, you suffer withdrawal until you resume. Even a Mistborn's stronger soul cannot escape this price.

#### Deepening Mastery (18th level)

Choose **two more** mastered metals you are not already a savant of; you become a savant of them as well, Dependency and all. Counting your starting quadrant, you are now a savant of most of the metals you wield, the equal of the greatest Allomancers in the histories, and as tethered to your metals as they were.

#### Mistborn Ascendant (20th level)

You are a Mistborn of the old stories. Your **Burn Budget is 32**, and:

- You are a **savant of every metal you burn**, not just your starting quadrant's. You ignore the per-metal flare cap on all sixteen and burn each with a savant's doubled efficiency; the only limits on how hard you burn are your Burn Budget and the metal in your body. You also bear a savant's **Dependency** for every metal, the price the greatest Allomancers always paid: cut off from a metal you were leaning on, you crash into withdrawal until you resume it.
- Once per **long rest**, you may perform a **free Duralumin dump**, detonating any metals you are burning without spending a duralumin charge.

---

### Quadrant Masteries
Your **starting quadrant** grants these four features, at 3rd, 6th, 10th, and 14th level. Each leans on the metals you know best and lets them work as one. Where a Mastery lets you exceed a Misting's limits, that is deliberate: a Mistborn's body and soul are nearer Preservation, and can bear what a lifelong specialist cannot.

\column

#### Physical (Iron, Steel, Tin, Pewter)

- **3rd — Braced Frame.** While you are **burning pewter**, your reinforced body bears the crushing recoil of your own Allomancy. You take no self-injury from bracing a Steelpush or Ironpull against something immovable, however hard you push, and you have advantage on saves to resist being moved or knocked prone. You must be burning enough pewter to withstand the force, but you do so with a little less metal than most. *(This shields you from the **crushing force** alone. Being shoved backward by recoil is a matter of your weight, not your toughness, and still applies.)*
- **6th — Mistborn's Bound.** While **burning steel or iron**, your movement turns unearthly. When you launch yourself off an anchor or Push and Pull to travel, you do not provoke opportunity attacks, you may act at the height of a leap, and you take no damage from a fall you guide with a Push.
- **10th — Overpush.** Because pewter lets your body bear it, you may push past a specialist's ceiling. Once on each of your turns, while **burning both steel (or iron) and pewter**, you may spend up to **twice your flare cap** in charges on a single Push or Pull, delivering the whole combined force in one blow. Pewter carries the crushing force; your **weight** alone decides how far the recoil throws you.
- **14th — Unbending.** You become a **savant of iron, steel, tin, and pewter**. Freed of their flare caps (bounded only by your Burn Budget and the metal in your body) and twice as efficient with each, you can loose Pushes and Pulls of staggering force, stretch your senses impossibly far, and drive your body to its very surge tier (the legendary resistance and might of high-flared pewter), so long as you have the pewter to survive them and the charges to spend. As a savant you also bear the **Dependency**: cut off from a Physical metal you were leaning on, you crash into withdrawal until you burn it again.

\page

#### Mental (Zinc, Brass, Copper, Bronze)

- **3rd — Sculpted Emotion.** Sweeping a room with feeling is easy; picking out one heart is the hard-won skill of the art. While **burning zinc and brass together**, you have that skill: you may **isolate and target a single specific emotion**, inflaming or soothing only it, **without the extra charge** it normally costs to differentiate one emotion from the rest. Where a lone Rioter or Soother must flood everyone, you touch exactly whom and what you mean to.
- **6th — Keen Seeker.** While **burning bronze**, you read Allomantic and magical pulses with rare clarity: you know the exact metal or power in use and its precise location, and you cannot be surprised by a creature using Allomancy, Feruchemy, or a spell within your bronze's reach. *(This does not make you a bronze savant, nor let you pierce a coppercloud; those still require what they always have, a savant's etched soul or duralumin-flared bronze.)*
- **10th — Deep Sway.** While **burning zinc or brass**, your emotional Allomancy takes a firmer hold. A creature that fails its save is swayed for a full minute rather than until the start of its next turn, and in an unhurried social scene you may move a creature's attitude up to **two** steps.
- **14th — The Quiet Court.** You become a **savant of zinc, brass, copper, and bronze**. Freed of their flare caps and twice as efficient with each, your coppercloud can swell to hide a whole company's Allomancy from even a savant Seeker, and your emotional pulses can reach and overwhelm every creature you can see for a hundred feet and more. The cost is always the charges you pour in, and a savant's **Dependency**: cut off from a Mental metal you were leaning on, you fall into withdrawal until you resume it.

\column

#### Temporal (Gold, Electrum, Cadmium, Bendalloy)

- **3rd — Oracle's Step.** While you sit within your own bendalloy or cadmium bubble and **burn electrum**, you read your near future in the stretched time: you always know a safe way out of the bubble, and you have **advantage on attack rolls against creatures outside it**, who crawl through slower seconds while you move freely.
- **6th — Nested Time.** You can hold **a bubble within a bubble.** Most usefully, when you trap foes inside a slow cadmium bubble, you may raise a smaller bubble of ordinary or quickened time **around yourself**, so that you act and react at full speed while your enemies are held in the crawl. Two nested rates of time are yours to manage, each at its own charge cost.
- **10th — Oracle's Reach.** While **burning electrum**, your own foresight runs deep and sure without your having to flare so hard for it: you cannot be surprised, you have advantage on Dexterity saving throws, and attackers you can see have disadvantage against you, the highest reach of an Oracle's sight made habitual.
- **14th — Master of the Moment.** You become a **savant of gold, electrum, cadmium, and bendalloy**. Freed of their flare caps and twice as efficient with each, you may, with charges enough, raise a bubble of such compression that a full minute passes within it for an eyeblink outside, as the Lord Ruler's servants once managed with a duralumin-fueled bendalloy, time enough to act, heal, flee, or prepare. It is never free, and it carries a savant's **Dependency**: cut off from a Temporal metal you were leaning on, you fall into withdrawal until you burn it again.
\page

## Feruchemist

*Where an Allomancer takes power from outside themselves and spends it, a Feruchemist only ever moves what they already are. They are frail this week so that they may be mighty on the day it matters, and they forget nothing, ever.*

A **Feruchemist** stores and taps **all sixteen** Feruchemical attributes, not just one. This is the art of the Terris, kept alive through generations of Keepers who filled copperminds with the whole memory of the world. This class turns that full inheritance into a character path.

> **How a Feruchemist works.** A Feruchemist uses the same Feruchemical economy as a Ferring: metalminds, storing and tapping, Rate and Depth, and compression. Each metal's actual attribute is on its Ferring page.

### Two hard restrictions

Feruchemy is inherited in the blood and trained from childhood, so it sits differently from an ordinary class.

- **Feruchemist must be your class at 1st level, and you cannot multiclass *into* it later.** You are born to the Terris line or you are not.
- **There is no exception.** Lerasium can make an Allomancer of anyone, but no god metal grants full Feruchemy. Where a Mistborn has one legendary back door, a Feruchemist has none.

(A Feruchemist may freely multiclass *out* into other classes; the restriction is only on entering.)

### Core Feruchemist Traits

**Hit Point Die:** D8 per Feruchemist level
**Saving Throw Proficiencies:** Constitution and Wisdom
**Skill Proficiencies:** Choose 2: Arcana, History, Insight, Investigation, Medicine, Nature, Perception, Religion, Survival
**Tool Proficiencies:** Calligrapher's supplies or smith's tools
**Weapon Proficiencies:** Simple weapons
**Armor Training:** Light armor
**Feruchemical Ability:** Constitution (save DC 8 + PB + Con)

*A Feruchemist's power is in what they carry. Rings, bracers, studs, and spikes are worth more to them than any blade.*

**Starting Equipment:** Choose A or B:
(A) **bracers** of each metal of your starting quadrant, each weighing 1d4 × 10 grams; **rings** of each other non-God metal, each weighing 2d4 grams; a **coppermind** ring; traveler's clothes, a scholar's pack, and 10 GP; or (B) 75 GP.

### The Feruchemist (level table)

{{classTable,frame,decoration,wide

| Level | PB | Features | Minds at Once | Quadrants | Compression |
|---|---|---|---|---|---|
| 1 | +2 | Feruchemy, Quadrant Mastery (1st), Keeper's Coppermind | 2 | 1 | 0.80 |
| 2 | +2 | Feruchemical Instinct | 2 | 1 | 0.80 |
| 3 | +2 | Quadrant Discipline | 3 | 1 | 0.80 |
| 4 | +2 | Ability Score Improvement | 3 | 1 | 0.80 |
| 5 | +3 | Quadrant Mastery (2nd) | 4 | 2 | 0.80 |
| 6 | +3 | Quadrant Discipline | 5 | 2 | 0.80 |
| 7 | +3 | Practiced Compression | 5 | 2 | 0.85 |
| 8 | +3 | Ability Score Improvement | 6 | 2 | 0.85 |
| 9 | +4 | Quadrant Mastery (3rd) | 7 | 3 | 0.85 |
| 10 | +4 | Quadrant Discipline | 8 | 3 | 0.85 |
| 11 | +4 | Deep Reserves | 9 | 3 | 0.85 |
| 12 | +4 | Ability Score Improvement | 10 | 3 | 0.85 |
| 13 | +5 | Quadrant Mastery (4th) | 11 | 4 | 0.90 |
| 14 | +5 | Quadrant Discipline | 12 | 4 | 0.90 |
| 15 | +5 | Unsealed Metalminds | 13 | 4 | 0.90 |
| 16 | +5 | Ability Score Improvement | 13 | 4 | 0.90 |
| 17 | +6 | Perfect Recall | 14 | 4 | 0.90 |
| 18 | +6 | Dumping | 15 | 4 | 0.95 |
| 19 | +6 | Epic Boon | 15 | 4 | 0.95 |
| 20 | +6 | The Metal Within | 16 | 4 | 0.95 |

}}

\page
### Class Features

{{tableGroup

#### Feruchemy (1st level)

You can store and tap **all sixteen** Feruchemical attributes, using the economy of the Ferring rules: metalminds worn, embedded, or swallowed; storing and tapping as free actions; Rate, Depth, and compression.

**Your Rate is a Ferring's Rate.** You can draw **+50% per level** without strain, exactly as a Ferring of your level. You are never a *deeper* tap than a specialist Ferring; your edge is breadth, not depth.

**Your Depth depends on mastery.** Depth is the hardest you can *store*, and it can never exceed 100%, since you cannot give up more of an attribute than you have.

| | Depth per level | Reaches 100% at | Rate |
|---|---|---|---|
| **Mastered quadrant** | 20% | **5th level** | +50% per level |
| **Unmastered quadrant** | 10% | 10th level | +25% per level (halved) |
| *(A Ferring, for comparison)* | 10% | 10th level | +50% per level |

}}

A mastered metal is stored and tapped exactly as its Ferring page describes, and you reach the **full 100% store at 5th level**, where an untrained Ferring waits until 10th. This is what a childhood of Terris training buys: not a deeper draw, but an earlier command of your own limits.

**This applies to every quadrant you master, not only your first.** Depth is measured against your character level, so a quadrant you master at 5th, 9th, or 13th arrives at the full 100% store immediately, since by then 20% per level has long since passed the ceiling. Only your **starting** quadrant reaches it *at* 5th level, and only because you had it from the beginning.

An **unmastered** metal is clumsy. Your Rate with it is **halved**, your Depth climbs at the slower pace above, and its compression is **one step harsher** than the value on your level table (0.80 becomes 0.70, and so on). You can use it in a pinch; you cannot rely on it.

**Capacity.** A metalmind holds **10 unit-minutes per gram**, where one unit-minute is 100% of the attribute held for one minute. Storing 20% of your strength for an hour banks 12 unit-minutes, and so does storing 100% of it for twelve.

**Minds at Once (breadth).** There is no limit to how many metalminds you may **own or carry**; a Keeper may travel under a hundred rings. What is limited is how many you can have **active at the same time**, meaning those you are actively filling or drawing from. That number equals the Minds at Once column of your level table, from 2 at 1st level to **16 at 20th**, where you can finally run every attribute at once.

This is the heart of a Feruchemist: a Ferring wears one ring and lives on one attribute, while you run health and strength and speed and wakefulness together. Metalminds merely worn, pocketed, or hoarded cost you nothing.

**God metals.** You store and tap the God Metals (the God Metals) as **mastered** metals **from 1st level**, at full Depth and full Rate, whatever quadrants you have taken. A god metal is pure Investiture rather than an ordinary alloy, so there is nothing in it to learn your way around; it answers as readily as breathing. They are held in check by their **extreme rarity**, not by any limit of yours.

At present this means **atium**, which stores **age**. A Feruchemist who comes into atium wields it fully at once, which is precisely why so few ever should.

{{tableGroup

#### Quadrant Mastery (1st, 5th, 9th, 13th levels)

The sixteen metals fall into four Feruchemical quadrants: **Physical**, **Cognitive**, **Hybrid**, and **Spiritual**. At 1st level, choose one to **master**; any of the four may be your starting quadrant. You gain three more masteries at 5th, 9th, and 13th level, choosing a new quadrant each time, until at 13th level you have mastered all four.

Your **starting quadrant** shapes you most, granting a **Quadrant Discipline** at 3rd, 6th, 10th, and 14th level. You do not choose a separate subclass; your first quadrant *is* your path.

| Quadrant | Metals | The path of |
|---|---|---|
| **Physical** | Iron, Steel, Tin, Pewter | The body: weight, speed, senses, strength |
| **Cognitive** | Zinc, Brass, Copper, Bronze | The mind: thought, warmth, memory, wakefulness |
| **Hybrid** | Cadmium, Bendalloy, Gold, Electrum | Endurance: breath, nutrition, health, determination |
| **Spiritual** | Chromium, Nicrosil, Aluminum, Duralumin | The soul: Fortune, Investiture, Identity, Connection |

}}

#### Keeper's Coppermind (1st level)

Whatever quadrant you begin with, you can always store and tap **copper**, treating it as **mastered**. You are a Keeper in the Terris tradition, and the memory of the world is your charge.

You begin play with a coppermind holding a memory your teacher thought you should carry. While you have a charged coppermind you may spend a minute consulting it to gain **proficiency in one skill or one language** recorded there, lasting until you next finish a long rest. What a coppermind holds is limited only by what has been filled into it, so the DM decides what a given mind knows.

\page

#### Feruchemical Instinct (2nd level)

Living by careful reserve teaches you to read your own limits exactly. You always know precisely how much is left in every metalmind you carry, to the minute, and you can judge at a glance roughly how charged **another** Feruchemist's metalmind is. You also have **advantage on saving throws against Exhaustion**.

#### Quadrant Discipline (3rd, 6th, 10th, 14th levels)

Your **starting quadrant** grants a **Discipline** at these levels, listed under Quadrant Disciplines below. These are the arts of endurance, preparation, and knowledge rather than of battle. A Feruchemist wins by having already prepared.

**A Discipline is never free.** Every Discipline refines how you *store or tap* one or more metals. To gain its benefit you must be storing or tapping the relevant metal as its Ferring page requires, and metalminds so used count against your **Minds at Once** as normal.

{{tableGroup

#### Practiced Compression (7th level)

Your control over drawing hard has grown. Your **compression value improves to 0.85**, as shown on the level table, and improves again at 13th and 18th level. This softens every draw you make past your Rate: where a Ferring loses a fifth of their store to reach twice their Rate, you lose less.

*(Recall from the Ferring rules: `tap duration = stored units × recovery ÷ tap intensity`, where recovery is your compression value raised to the power of `multiple − 1`. A better compression value means a longer draw at every multiple.)*

| Multiple of your Rate | 2× | 3× | 4× | 5× | 8× |
|---|---|---|---|---|---|
| Recovery at **0.80** | 0.80 | 0.64 | 0.51 | 0.41 | 0.21 |
| Recovery at **0.90** | 0.90 | 0.81 | 0.73 | 0.66 | 0.48 |
| Recovery at **0.95** | 0.95 | 0.90 | 0.86 | 0.81 | 0.70 |

}}

#### Deep Reserves (11th level)

You have learned to fill more into less. The **capacity of every metalmind you fill is doubled**, holding 20 unit-minutes per gram rather than 10. Minds filled by others are unchanged; this is a property of your storing, not of the metal.

#### Unsealed Metalminds (15th level)

You can make a metalmind that belongs to **no one**, so that a person with no Feruchemy at all may tap the health, strength, or speed you banked for them.

**A metalmind cannot be unsealed after the fact.** A mind is keyed to whoever filled it, at the moment it is filled; there is no way to strip that key off later. An unsealed mind must be made unsealed **from the very first charge**, which is why so few exist.

**Making a gift metalmind.** The full procedure has three parts, and you must hold the first throughout.

1. **Store 100% of your Identity** into an aluminummind, and keep it stored for the whole of the work. With no self to leave a mark, nothing you fill carries a key. This demands **100% Depth** in aluminum, and while you do it you are hollow and dangerously open to charm, possession, and alteration (see the Trueself page).
2. **Store the ability itself into nicrosil.** Fill a nicrosilmind with your ability to use the metal in question, so the recipient has the power to draw at all. You cannot use that ability yourself while it is banked.
3. **Store a reserve of the attribute** into a mind of that metal, still with your Identity fully stored, so there is something for them to draw.

**The usual construction** is a single object: a body of the primary metal, carrying the attribute, with a **small piece of nicrosil worked into its surface**, carrying the ability. The recipient taps the ability from the nicrosil and the attribute from the body beneath, and so wields an art they never learned, for exactly as long as the mind lasts.

A creature tapping a gift metalmind draws at **your** Rate or their own, whichever is lower, and gains no other part of your training.

*If **Spiritual** is your starting quadrant, you gain this feature at 6th level instead; see the Spiritual Disciplines below.*

#### Perfect Recall (17th level)

Your copperminds have become a second mind, and you move through them as easily as through your own thoughts. You may draw a memory from any coppermind you carry as a **free action** rather than over a minute, and copperminds you are drawing from **do not count against your Minds at Once**.

You also keep a perfect **index**. A stored memory is genuinely gone from your head while it sits in the metal, as it is for every Archivist, but you always know **exactly what you have stored and which mind holds it**, and you can never be confused or deceived about your own catalog. No magic can alter, steal, or read a memory while it rests in copper.

#### Dumping (18th level)

Your compression improves to **0.95**, and you learn the hardest trick in the art: to **empty a metalmind all at once**.

As an action, you may **dump** a single metalmind, drawing its entire remaining contents in one second rather than over its natural span. You gain the whole of what it held, at whatever colossal intensity that implies, and **compression does not apply**: the mind gives up everything it has, wasting nothing. The metalmind is left completely empty.

\page

You may dump once per **long rest**. A dumped attribute is still bound by its own nature, so the Ferring page limits still hold: a dumped pewtermind cannot make you larger than your frame will bear, and a dumped goldmind cannot mend what gold could never mend. Within those limits, a Feruchemist who has spent a year filling a ring can spend it all in a heartbeat.

**Notable dumps.** Every attribute has its own version of the moment.

| Metal | What a dump does |
|---|---|
| **Duralumin (Connection)** | The famous one. The surge binds you to **everyone in the area** at once, and a deep enough store pulses further still, out into the wider world, so that for a time strangers who have never met you regard you as someone they know of and reckon with. It is the likeliest explanation for why certain wanderers are famous in lands they have never walked. |
| **Gold (health)** | Every banked hit point lands at once. Mortal wounds close in a heartbeat, though nothing gold could never mend is mended. |
| **Pewter (strength)** | A single instant of overwhelming might, bounded by what your frame can bear before it tears itself apart. |
| **Steel (speed)** | A blur of motion for a few seconds, until air resistance sets its own hard ceiling. |
| **Aluminum (Identity)** | You become wholly and adamantly yourself, throwing off possession, transformation, and every alteration at once. |
| **Chromium (Fortune)** | A surge of luck spent in one impossible moment. |
| **Brass (warmth)** | Every stored kilojoule released at once. This is as dangerous to bystanders as to you, and is closer to an explosion than a gift. |

**What cannot be dumped.** Attributes that are not intensities have nothing to compress into an instant. **Reserve** attributes (breath, nutrition) are pools you draw down at a natural rate, and **copper** holds discrete memories rather than a quantity. Dumping these simply empties them to no special effect.

#### The Metal Within (20th level)

You have kept so much of yourself in metal for so long that a little of it stays without the metal. Choose **two** attributes you have mastered. You can **store and tap those two without a metalmind at all**, holding their reserve in your own soul.

- Each such reserve holds **10 unit-minutes**, and what you have not spent is still there when you finish a long rest. It cannot be given away or taken from you.
- These soul-held reserves do not count against your **Minds at Once**, which is **16**, enough to run every attribute in Feruchemy at the same time.

*This is not savanthood. A true Feruchemical savant is made only through relentless Compounding, drawing on power from outside oneself, and pays a dependency for it. What you have instead is the quiet mastery of a lifetime: no cost, no craving, and no metal required.*

---

### Quadrant Disciplines
Your **starting quadrant** grants these four features, at 3rd, 6th, 10th, and 14th level. They lean toward survival, preparation, and knowledge, which is where a Feruchemist's true strength lies.

**Feruchemy only ever acts on the Feruchemist.** A tapped attribute is yours and cannot be lent, projected, or shared. The single exception is **brass**, because warmth genuinely radiates off a body into the air around it. Everything else reaches other people only through an unsealed metalmind handed over for them to tap themselves.

**Everything is an economy.** Each Discipline below spends something real: unit-minutes from a mind, kilojoules of warmth, hit points of banked health. Nothing here is a free passive.

\page
#### Physical (Iron, Steel, Tin, Pewter)

- **3rd — Tireless.** While tapping pewter, even at the slightest draw, your borrowed strength carries you where endurance alone would fail. You ignore the movement cost of difficult terrain, you can march for twice the normal hours before risking Exhaustion, and you have advantage on saving throws made to resist Exhaustion from exertion. Tapping strength is what does this; no other Physical metal substitutes for it.
- **6th — Feather and Stone.** You have mastered your own weight, in both directions. While **storing** iron you are lighter than you should be: you reduce all falling damage by **the equivalent of 10 feet for each 10% of your weight stored** (at a full 100% store you simply drift down and take none), and you may cross surfaces that would never bear you, such as thin ice, rotted boards, a rope bridge, or deep snow. While **tapping** iron you are immovable: you have advantage on saving throws and contests against being pushed, pulled, knocked prone, or thrown, including against a Coinshot's Steelpush.
- **10th — Second Wind of the Body.** While tapping pewter, you may spend **5 unit-minutes** from a pewtermind as a bonus action to shrug off a moment of failure: end one effect on yourself causing the Paralyzed, Restrained, Slowed, or Stunned condition, or reduce your Exhaustion by one level. There is no limit on how often you may do this beyond what your metalminds hold, for the cost is the limit.
- **14th — The Body Remembers.** Physical metalminds you are actively drawing from **count as half a mind each** against your Minds at Once, so you can run all four Physical attributes for the price of two. While tapping three or more Physical metals at once, you have **resistance to bludgeoning, piercing, and slashing damage from nonmagical sources**.

\column

#### Cognitive (Zinc, Brass, Copper, Bronze)

- **3rd — Keeper's Index.** You have organized your copperminds as the Keepers do. You may search all copperminds you carry for a specific fact as a free action, and you always know whether a thing you seek is stored in them. You gain proficiency in **two additional skills** from the Feruchemist list, representing the breadth of what you have read.
- **6th — Quickened Thought.** While tapping zinc, your speed of thought sharpens your reactions: you have **advantage on Initiative**, and once per round you may take the Search or Study action as a bonus action. You may also solve in seconds a problem that should take minutes of study.
- **10th — Hearth and Hoard.** Warmth is the one thing a Feruchemist can genuinely give away, because heat radiates from you whether you mean it to or not. While tapping brass, you may pour out warmth to shelter others: spend **500 kJ per minute for each creature** within 30 feet you wish to keep comfortable in natural cold, and **1,500 kJ per minute each** to grant them **resistance to cold damage**. These figures already include your discount: you have learned to shape that radiance rather than let it bleed away, so warming others costs you half what it costs anyone else. *(The figures come from the body's own arithmetic on the Firesoul page: roughly 500 kJ is one step of body-temperature imbalance, about a minute's worth of serious cold. A 10th-level Firesoul's throughput of some 8,000 kJ per minute can shelter a large party, or armor a few against real freezing, but not both without emptying rings fast.)*
- **14th — The Whole Library.** Your mind and your metal are one archive. You have **expertise** in Arcana, History, Nature, and Religion. Once per long rest, while tapping copper, you may recall a fact no living person should know, whatever a Keeper before you thought worth storing, and the DM tells you something genuinely useful about the situation at hand.

\page

#### Hybrid (Cadmium, Bendalloy, Gold, Electrum)

- **3rd — Provisioned.** Your bendalloyminds and cadmiumminds make **you** self-sufficient, as Feruchemy always does and only ever can. While tapping bendalloy you need no food or water and suffer nothing from starvation or thirst, and while tapping cadmium you can go without breathing indefinitely, functioning in thin, foul, drowned, or absent air. You have also learned to fill these minds from any source you can get down, so a single enormous meal or a lungful of pressurized air banks far more than it should. *(What you cannot do is feed or breathe for anyone else. A tapped attribute is yours alone.)*
- **6th — The Long Convalescence.** Your control of gold has grown fine enough to cheat death cleanly. When you tap gold to survive a killing blow, the usual **2-for-1** cost becomes **1-for-1**: you pay just **1 hit point from the ring for each 1 you were driven below 0**, staying at 0 hit points, conscious, and able to act. A charged goldmind now buys you exactly its own worth in punishment absorbed.
- **10th — Unbreakable Will.** While tapping electrum, nothing turns you aside. You are **immune to the Frightened and Charmed conditions**, you automatically succeed on saving throws to maintain a course of action against magical compulsion, and you may continue acting for one round at 0 hit points before falling unconscious.
- **14th — Deathless.** Gold, cadmium, and bendalloy that you are drawing from **do not count against your Minds at Once**, so health, breath, and sustenance run free alongside everything else you are doing. While all three run, you need not eat, drink, or breathe, and you can absorb a truly absurd amount of punishment: **spend 1 hit point from a goldmind for each 1 point of damage that would drop you below 0**, remaining conscious and acting for as long as the gold holds out. You die when the ring runs dry and not before. A Feruchemist so provisioned walks out of a desert, a sealed tomb, or a battlefield that killed everyone else. *(This buys endurance, not youth. Reversing your age is atium's domain, and only through Compounding.)*

\page
#### Spiritual (Chromium, Nicrosil, Aluminum, Duralumin)

*Beginning with the Spiritual metals means beginning with the strangest and most coveted art in Feruchemy: the making of metalminds that belong to no one.*

- **3rd — Blank Slate.** You have learned to hollow yourself early and safely. While your Identity is stored in aluminum, effects that seek out *who you are*, by name or by soul, simply fail to find anyone there, including scrying and most divination. *(Identity is not Connection, which is duralumin's domain, but a person with no self to name is hard to reach by either road, so a full store muffles Connection-seeking magic as well.)* Storing Identity normally leaves you wide open, imposing **disadvantage on saving throws** against being Charmed, possessed, disguised over, or transformed. You **no longer suffer that disadvantage**, having learned to keep a thread of yourself back, unless the work demands you empty yourself completely, as Unsealed Metalminds does.
- **6th — Unsealed Metalminds.** You gain the Unsealed Metalminds feature, nine levels early, with its full procedure: **100% of your Identity stored** throughout, the **ability banked into nicrosil**, and a **reserve of the attribute** filled alongside it, usually as one object of the primary metal with a sliver of nicrosil at its surface. You can do this at 6th level because a mastered quadrant reaches **100% Depth at 5th**, and Spiritual is yours from the beginning. From here on you can hand your banked health, strength, or speed to anyone at all, even someone with no Feruchemy in their blood. This is the signature of a Spiritual Feruchemist, and the reason the Southern Scadrians could arm a whole people with borrowed power.
- **10th — Borrowed Craft.** With your Identity fully stored, you carry no self to clash with the lock on another's metalmind. You may **tap the keyed metalminds of other people** as though they were your own, drawing out any power you could already wield yourself, and you need not have their consent if you can lay a hand on the mind. A Feruchemist can drain an enemy's banked strength, or spend a fallen ally's goldmind to save them. You cannot draw out a power you could not otherwise use: to take someone's stored strength, you must be able to tap a pewtermind yourself.
- **14th — Threads of Connection.** While tapping duralumin, you may forge a Connection to a **person** rather than to the land, and through them you speak and understand **any language they know**, for as long as you keep tapping. Once per long rest you may tap deeply enough to bind yourself to a place or a person in earnest, gaining **advantage on all Charisma checks** with that community or individual for one hour, and you may tap chromium to turn one failed **Charisma** saving throw or ability check into a success.

 **Many Selves.** You have learned that Identity is not one thing but a garment, and you keep a wardrobe. You may maintain **several distinct Identities**, each held in its own aluminummind, and change which one you are wearing as an action.

 - A metalmind you fill is keyed to **the Identity you wore while filling it**, not to your body. You can therefore carry minds that only *you-as-someone-else* can tap, and no one who compels or copies your present self can reach them.
 - Whenever you change Identity, any effect tracking you by name, soul, or Connection **loses you outright**, as though the person it sought had ceased to exist. Divination that finds you must find your current self, and must find it again each time you change.
 - You always know which self you are wearing and cannot be made to forget the others. This is a wardrobe, not a fracture.

 A Spiritual Feruchemist at this level is, in the most literal sense available to the art, no longer any particular person.

---

{{tableGroup

### Feruchemist and Ferring

A Feruchemist is not simply sixteen Ferrings. Set side by side at the same level:

| | Ferring | Feruchemist |
| ------------------------ | --------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Metals** | One | All sixteen (mastery by quadrant) |
| **Rate** (tap intensity) | +50% per level | **+50% per level, the same** |
| **Depth** (max store) | 10% per level, 100% at 10th | 20% per level in a mastered quadrant, **100% at 5th**, and 10% per level in each other metal. |
| **Minds at once** | One attribute | **2 at 1st, 16 at 20th** (every attribute at once) |
| **Compression** | 0.80 | 0.80, improving to **0.95** |
| **Unsealed minds** | Never | Yes (15th, or 6th for a Spiritual start) |

}}

The Feruchemist never draws *harder* than the specialist. They simply draw from everywhere at once, and they have already prepared.
\page

## Hemalurgist

*Allomancy is a gift and Feruchemy is an inheritance. Hemalurgy is neither. It is a craft, learned the way surgery is learned, and every practitioner who ever mastered it did so over a great many bodies.*

A **Hemalurgist** has no power of their own. What they have is **knowledge**: which metal steals which attribute, where on a body it must be driven, and how to arrange spikes in a living frame so the frame survives. With that knowledge they can take a power from one person and give it to another, including themselves.

This is the art of **Ruin**, and it is **end-negative**. Investiture is always lost in the transfer, the recipient's soul is left punctured, and the donor is always dead. There is no version of this that is clean.

### Core Hemalurgist Traits

**Hit Point Die:** D8 per Hemalurgist level
**Saving Throw Proficiencies:** Constitution and Intelligence
**Skill Proficiencies:** Choose 2: Arcana, Deception, Insight, Investigation, Medicine, Perception, Religion, Sleight of Hand
**Tool Proficiencies:** Smith's tools and one of: alchemist's supplies, tinker's tools, or a surgeon's kit
**Weapon Proficiencies:** Simple weapons, plus spikes and picks
**Armor Training:** Light and medium armor
**Hemalurgic Ability:** Intelligence (save DC 8 + PB + Int)

*Your power is what you know and what you have built. A Hemalurgist's real arsenal is a roll of prepared spikes and an accurate map of the human body.*

**Starting Equipment:** Choose A or B:
(A) a **spike-maker's kit** (smith's tools and a surgeon's kit), **six blank spikes** of assorted non-God metals, **one charged spike** of the DM's choosing and origin, a set of anatomical charts, leather armor, a dagger, and 10 GP; or (B) 75 GP.

# The Hemalurgist (level table)

{{classTable,frame,decoration,wide

| Level | PB | Features | Spikes Borne | Yield Floor |
|---|---|---|---|---|
| 1 | +2 | Hemalurgy, Spike Craft, Placement | 1 | 60% |
| 2 | +2 | Anatomist's Eye | 1 | 60% |
| 3 | +2 | Hemalurgic Practice | 2 | 60% |
| 4 | +2 | Ability Score Improvement | 2 | 60% |
| 5 | +3 | The Linchpin | 3 | 60% |
| 6 | +3 | Practice feature | 3 | 60% |
| 7 | +3 | Preserved Charge | 4 | 60% |
| 8 | +3 | Ability Score Improvement | 4 | 60% |
| 9 | +4 | Efficient Splicing | 5 | 70% |
| 10 | +4 | Practice feature | 5 | 70% |
| 11 | +4 | Deep Placement | 6 | 70% |
| 12 | +4 | Ability Score Improvement | 6 | 70% |
| 13 | +5 | Refine God Metal | 7 | 70% |
| 14 | +5 | Practice feature | 7 | 70% |
| 15 | +5 | Clean Extraction | 8 | 75% |
| 16 | +5 | Ability Score Improvement | 8 | 75% |
| 17 | +6 | Master of the Work | 9 | 75% |
| 18 | +6 | Unfailing Placement | 9 | 80% |
| 19 | +6 | Epic Boon | 9 | 80% |
| 20 | +6 | The Eleventh Spike | 11 | 80% |

}}

**Spikes Borne** is how many spikes *you* can carry in your own body without dying, and it is the only spike count this class caps.

**Yield Floor** is the minimum strength of a spike you charge, explained under Spike Craft. Better craft wastes less soul.

\column

**How many spikes you can make is not limited.** Given metal, time, and donors, a Hemalurgist can produce hundreds, and history's worst of them did. The limits on the art are supply, opportunity, and whatever conscience the practitioner has left. What *is* fixed is how many a single body can hold.

\page
### Class Features

#### Hemalurgy (1st level)

You know how to steal a piece of a soul and graft it onto another. Three things govern every use of the art.

**Metal decides what is stolen.** Each metal takes a different category of attribute or power, listed under What Each Metal Steals.

**Placement decides the specifics.** The same metal driven into two different places on a body yields two different results. The body holds somewhere between two and three hundred of these **bind points**, and no one has ever mapped them all. What is known is written down; the rest is guesswork paid for in bodies.

**Intent is required.** A spike cannot be made by accident. The intent to steal must be present, though it need not be *yours*: a spike driven by a puppet, a trap, or a thrown weapon still charges, so long as someone meant it to.

**Spikes Borne.** You may carry a number of spikes in your own body equal to the Spikes Borne column. This limit is not toughness; it is **knowledge of stable configurations**, of how spikes may be arranged in a living body so that the body holds together. Exceeding it is not a penalty but a death: a body given more punctures than its configuration can support fails, usually within minutes.

**The eleven-spike ceiling.** No body, however expertly configured, holds more than **eleven** spikes. This is a fact about people, not about your skill, and it applies to you, to your allies, and to every construct and Inquisitor you will ever meet. Beyond eleven, the Spiritweb has too little left of itself to hold anything, and further spikes grant nothing at all even if the body survives them. Any bearer taking a **fourth** spike or more also requires a linchpin, or they will simply die of it.

**Stolen Feruchemy carries its keys.** If you steal a *Feruchemical* power from a donor, you also gain the ability to tap **that donor's own metalminds**, their Identity no longer barring you.

{{tableGroup

#### Spike Craft (1st level)

Making a spike takes a metal, a donor, and a killing.

**Charging a spike.** Drive a prepared spike of the chosen metal through a donor's **heart**. This is the universal charging point, it works for any metal and any attribute, and it kills the donor. Every spike that has ever mattered was made this way.

**Yield.** Investiture is always lost in the transfer, so no spike carries the whole of what it took. When you charge a spike, roll **1d100** to determine what percentage of the donor's power it holds. The donor sets the band, and your **Yield Floor** raises the bottom of it.

| Donor | Grade | Yield band | What it can take |
|---|---|---|---|
| A **person** (human or other fully sapient being) | **Full** | Your Yield Floor to 100% | Anything: any Metallic Art, any innate attribute |
| A **humanoid monster** or lesser sapient creature | **Lesser** | 30% to 60% | Only powers and attributes the donor actually possessed, and never above what the donor itself could do |
| An **animal** | **Crude** | 10% to 30% | Innate physical attributes only (strength, senses, toughness). Never a Metallic Art |
| A **recovered spike** | **Decayed** | The DM sets it | Whatever survived. Found only where Hemalurgy was practiced: Inquisitor barrows, old Ministry sites, a koloss battlefield |

}}

*Read the roll against the band: treat any result below the band's floor as the floor, and any result above its ceiling as the ceiling.* A spike at 80% grants its power at 80% strength. For a Metallic Art this means a **bloodline level** (the level at which a Misting or Ferring power scales, normally equal to the bearer's character level; see Misting Bloodlines) of 80% of the bearer's own level, rounded down, minimum 1.

*Hemalurgy works on animals but never on plants, and it transmits no disease or infection, however filthy the working.*

**Hemalurgic decay.** A spike out of a body **loses potency steadily**, dropping its yield over weeks at a rate the DM sets. Keeping it embedded in *someone* stops the loss entirely. **Coating it in blood** significantly slows it, which is why spikes are stored in sealed jars of the stuff. Splitting a spike divides its charge **and loses some of it**.

\page
{{tableGroup

#### Placement (1st level)

Driving a charged spike into a recipient takes **1 minute** of careful work on a willing, unconscious, or restrained subject, and it is the moment everything can go wrong.

Make an **Intelligence (Medicine) check** against **DC 10, plus 2 for each spike already in that body**.

| Result | Outcome |
|---|---|
| **Success** | The spike takes. The recipient gains its power at the spike's yield. |
| **Fail by 1 to 4** | The spike takes badly. It grants **half** its yield, and the recipient takes **4d10 piercing damage**. |
| **Fail by 5 or more** | The spike does not take. Its **charge is lost entirely**, and the recipient takes **6d10 piercing damage**. |
| **Fail by 10 or more** | As above, and the recipient must succeed on a **DC 15 Constitution saving throw** or **die**. |

}}

You know the placements that are actually written down, so you make this check with **advantage** when placing a spike whose metal and intended effect appear on the Known Placements table. Anything else is a guess.

Placing a spike in an unwilling, conscious creature is not a surgery but an attack; see Master of the Work.

**Removing a spike** removes its power. Doing so takes 1 minute and deals **2d10 piercing damage** to the bearer. Removing a **linchpin** kills, with no check and no save.

#### Anatomist's Eye (2nd level)

You have opened enough bodies to read them from the outside. You can spot the work: the hard line of metal under a collar, the particular gait of someone whose frame is held together with spikes.

- As an action, study a creature within 30 feet and make an **Intelligence (Investigation) check** against DC 12, or against the creature's Charisma (Deception) check if it is deliberately concealing its spikes. On a success you learn **how many spikes it bears and roughly where they sit**.
- You have **advantage on Intelligence (Investigation) checks** to work out whether a creature has been using magic or a Metallic Art, reading it from burns, residue, pupil dilation, and the state of their hands. This is deduction, not sense. It tells you nothing a Seeker would know, and a creature doing nothing gives you nothing.

#### Hemalurgic Practice (3rd, 6th, 10th, 14th levels)

Every Hemalurgist eventually decides what the work is *for*. Choose a **Practice** at 3rd level: The Spiked, The Fleshwright, or The Bestower. It grants features at 3rd, 6th, 10th, and 14th level.

#### The Linchpin (5th level)

You have learned the configuration that makes real Hemalurgy survivable: a single spike driven into the upper back, between the shoulder blades, which **binds all the others** and holds a fraying Spiritweb together.

- A recipient with a linchpin can bear **four or more** spikes without their body failing. Without one, a fourth spike is death.
- **Removing a linchpin kills the bearer**, immediately, with no check and no saving throw. This is true of you, of your creations, and of any enemy Inquisitor you can reach, which cuts both ways.

> **The one known loophole.** A bearer who can **Compound gold** heals faster than the unmaking kills. Such a person could, in principle, have their spikes drawn out one at a time, mending each wound as it opens, and take the linchpin last of all, surviving the removal of every spike they carry. It has almost certainly never been done, and it is the DM's to allow.

#### Preserved Charge (7th level)

You have solved decay, or near enough. After enough ruined spikes you have worked out what the Arcanists eventually would: a spike sealed inside a **casing of aluminum** stops decaying entirely, the metal that resists all Investiture holding the charge in place.

Spikes you seal this way **do not decay at all** while sealed, and you may treat a blood jar as indefinite storage rather than merely slowing the loss. Your stockpile becomes real property rather than a wasting asset.

*(The method is your character's own discovery. In the histories it is only ever guessed at.)*

#### Efficient Splicing (9th level)

Your cuts waste less soul. Your **Yield Floor rises to 70%**, and it rises again at 15th and 18th level. In addition, a **Lesser** spike you charge uses a band of 40% to 80% rather than 30% to 60%, making humanoid monsters a genuinely useful source rather than a poor substitute.

#### Deep Placement (11th level)

Your map of the body has passed what anyone has written down. You have **advantage on every Placement check**, on any body of any species, whether or not the effect you intend appears on the Known Placements table. You may also attempt placements no one has recorded: describe the effect you are reaching for, and the DM sets a DC and tells you what you find. This is how the table gets longer.

#### Refine God Metal (13th level)

You can **refine atium** into a workable spike, and use it. An atium spike is a wild card: it steals **any** power, chosen at charging, and does so more effectively than the metal proper to that power, taking it at **100% yield** regardless of the donor. Lerasium may likewise be spiked, stealing **all** of a donor's abilities at once, though doing so wastes most of a bead that could have made a Mistborn outright.

\page
#### Clean Extraction (15th level)

Your **Yield Floor rises to 75%**, and you have learned to take a spike out as carefully as you put it in. Over 10 minutes of work you may remove a spike from a living bearer **without dealing any damage**, leaving them whole and merely diminished by the loss of the power. A linchpin remains fatal to remove, and nothing you know changes that.

#### Master of the Work (17th level)

Spiking is second nature. You may place a spike in a willing or Incapacitated creature as an **action** rather than over a minute, and you may drive one into an unwilling creature as part of the Attack action, using a spike as a melee weapon (1d6 piercing, finesse) that delivers its charge on a hit. A spike delivered by attack still requires a Placement check, made without advantage unless another feature grants it.

#### Unfailing Placement (18th level)

Your **Yield Floor rises to 80%**. You no longer miss. You **automatically succeed** on Placement checks, on any body, known placement or not, and you may **relocate** a spike already in a creature to a different placement of the same metal, changing what it grants.

#### The Eleventh Spike (20th level)

You have found the configuration the Lord Ruler's steel priests used. You may become, or make, a **Steel Inquisitor**.

- Your **Spikes Borne is 11**, the full Inquisitor complement.
- **Steel sight.** A spike driven through an **eye socket** lets you see through the spike rather than the eye, perceiving metal and living bodies through walls out to 120 feet. A single spiked eye is enough for this. With **both** eyes spiked you also perceive **sources of Investiture**, and you can read a creature's Invested signature clearly enough to **tell individuals apart by it**, through disguise, through darkness, and through walls. You cannot be Blinded.

**What Inquisitors were made of.** An Inquisitor's legendary durability was never a property of having spikes. It came from what the spikes let them **Compound**: pewter for strength and a body that would not break, gold for wounds that closed as fast as they opened, atium for a face that never aged. If you want that, take the matched pairs and pay for them like anyone else. Eleven slots is enough to hold a great deal.

**The price is total.** An eleven-spiked Spiritweb is more hole than soul. You have **disadvantage** on every saving throw against being Charmed, Frightened, or controlled, and against emotional Allomancy of any kind. Against a **strong Soother or Rioter** you succeed only on a natural 20. Against **a Shard, or any being of that order**, you do not get a saving throw at all; whether it chooses to take you, and what it does with you, is entirely the DM's to decide.

*This is what an Inquisitor is. The power is real and so is the leash.*

---

{{tableGroup

### Control Risk

Every spike punches a hole in the soul it enters. Through those holes, things reach in.

This applies to **anyone** carrying spikes, including you, your allies, and your creations. Track it by **number of spikes borne**.

| Spikes | Vulnerability |
|---|---|
| **1** | A hole, but a small one. You have **disadvantage on saving throws against emotional Allomancy** (Rioters and Soothers). A god cannot reach you. |
| **2–3** | The holes connect. As above, and a **Shard or similar power may attempt to influence you**: when it does, make a Wisdom saving throw against a DC the DM sets. On a failure you feel its intent as your own idea for a time. |
| **4–6** | Wide open. As above, with **disadvantage** on those Wisdom saves, and a controller who has taken hold of you **keeps that hold** without further effort until it is broken. |
| **7–8** | Barely your own. As above, and any creature attempting control has **advantage**, while you succeed on such saves only on a 17 or higher. |
| **9–11** | Inquisitor. See The Eleventh Spike. Against a strong Soother or Rioter you succeed only on a **natural 20**; against a Shard you get **no save at all**. |

}}

**What helps.**

- **Mental fortitude resists.** A **copper** spike steals exactly that, and a bearer carrying one has **advantage** on all saving throws against control. This is why the kandra Blessing of Presence was so valued. It is the single best investment a heavily spiked character can make.
- **Strong emotion makes control easier.** A bearer who is enraged, terrified, or grieving takes **disadvantage** on control saves regardless of spike count.
- **Control, once seized, persists** without further Soothing or Rioting, and a **stronger controller can steal it** from a weaker one. Being someone's puppet does not protect you from becoming someone else's.
- **Aluminum** worn over the head blocks emotional Allomancy as it always does, though it does nothing against a Shard.

---

\page
{{wide
## What Each Metal Steals

::::

{{wide
<!--h:44-->
![chart-hemalurgy](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/chart-hemalurgy.svg?v=e7224f2c){width:100%}
}}

| God metal | Steals |
|---|---|
| **Atium** | Any power, at full yield. Must be refined (13th level) |
| **Lerasium** | All of a donor's abilities at once |
| **Trellium** | Unknown, and not of this world. Makes Chimeras |

}}

A stolen Allomantic or Feruchemical power makes its bearer a Misting or Ferring of that metal, using the Misting or Ferring page as written, at a bloodline level equal to the spike's **yield percentage of the bearer's own level**, rounded down, minimum 1.

**Stealing a spellcaster's power** is possible, and is set out in The Metallic Arts and the Weave rather than here, because a table playing without that appendix has no spellcasters for a Hemalurgist to steal from.

**Hemalurgy is physically destructive.** A single spike is just a spike, and leaves its bearer looking like a person with a spike in them. It is *stacking* them that twists a body, and worst of all when the stolen attribute is neither Allomantic nor Feruchemical. Raw strength, senses, and fortitude deform the most, which is why koloss look as they do and Inquisitors are unmistakable.

{{tableGroup

#### What Each Creation Requires

| Creation | Requires |
|---|---|
| **Koloss** | Four iron spikes of human strength, driven into a living humanoid |
| **Hemalurgic Chimera** | One trellium spike |
| **Kandra** | Two matched spikes in the shoulders of a Mistwraith, a **Blessing**. Only the Lord Ruler ever knew how to create one |
| **Steel Inquisitor** | Nine to eleven spikes and a linchpin. Seekers and Mistborn are the preferred base, since stacked bronze pierces copperclouds |

}}

---

\page
## Hemalurgic Practices

#### The Spiked

*You are the work. Every configuration you find, you find on yourself.*

- **3rd — Self-Surgery.** You can place a spike in your own body without assistance, however awkward the placement, and you **automatically succeed on the Placement check** to do so. When you do, make a Constitution saving throw (DC 10 + the number of spikes you already bear) to remain conscious through it; on a success you may act immediately, and on a failure you fall unconscious for 1 minute.
- **6th — Honed Intent.** You have learned to sharpen the intent behind the killing, and the soul comes away more whole. For spikes **you** charge, your **Yield Floor is 80%**, or your usual floor if that is higher. A spike you make is worth two that you find.
- **10th — Reinforced Frame.** Your body has learned to carry metal. Your **Spikes Borne increases by 1**, and you have advantage on saving throws against effects that would remove, move, or disable your spikes, including a Leecher's touch. *(Metal inside a living body cannot be Pushed or Pulled at all by ordinary Allomancy. Only a duralumin-flared burn or a lerasium-made Mistborn has ever managed it, and against those you at least get the save.)*
- **14th — Terrible Symmetry.** Your **Honed Intent floor rises to 90%**. Your spikes have also become the most visible thing about you: creatures that can see them have **disadvantage on saving throws against being Frightened by you**.

\column

#### The Fleshwright

*You make things. Some of them were people once.*

- **3rd — Koloss-Making.** You know the four-iron-spike configuration that makes a Koloss. Given four iron spikes of human strength and a living humanoid, willing or not, you can make one over an hour of work, using the koloss statistics the DM provides. It grows continuously and will eventually die of it.

 **What limits you is command, not spikes.** You can make as many koloss as you have spikes and victims for, but you can hold the obedience of only **your Intelligence modifier + your proficiency bonus** of them at once. Koloss beyond that number **go feral**, attacking whatever is nearest, and are as dangerous to you as to anyone. This is how koloss hosts have always ended.
- **6th — Chimera-Making.** If you possess **trellium**, you know the single-spike configuration that makes a **Hemalurgic Chimera**: a quadrupedal, canine-twisted thing with a thickened skull, hidden from a Shard's sight by the very spike that made it. A Chimera **cannot be commanded**. It can only be **contained and released**, and it does not distinguish friend from enemy once loose. It does not count against your command limit, because you never had it. Trellium is not of this world and is the DM's to place.
- **10th — Placing the Blessings.** The making of a **Blessing** died with the Lord Ruler, and you have not recovered it. What you have recovered is how to **place** one. Given an intact Blessing (a matched pair of spikes, which is treasure the DM must provide) you can implant it in a Mistwraith over an hour of work, making it a Kandra. A kandra bears only two spikes, so it is nearly impossible for anyone to control, including you. What you get is not a servant but a person, who will remember who made them.
- **14th — The Steel Priest's Art.** Your creations hold together as no one else's do.
 - Every construct you make may bear a **linchpin**, and therefore up to the full eleven spikes.
 - Your **command limit doubles**, and a koloss of yours that would go feral instead stands **inert** until you attend to it.
 - Your intent sits in your creations' spikes the way an Allomancer's does. Any creature attempting to control one of them must first succeed on a check against your Hemalurgy save DC, as though **wresting the control away from you**, and you may issue commands to any creation whose location you know, at any distance.
 - When you spend an hour restoring a damaged construct, replacing lost flesh and re-seating loose spikes, it regains all its hit points and gains temporary hit points equal to your Hemalurgist level.

\page

#### The Bestower

*The spikes go into other people. That has always been where the real power was.*

- **3rd — Careful Gift.** When you place a spike in a **willing** creature, the wound is clean. You automatically succeed on the Placement check, they take no damage from it, and they count as having **one fewer spike** for Control Risk, to a minimum of one. Your allies can be armed without being ruined.
- **6th — Shared Arsenal.** You can move a spike from one willing bearer to another in **1 minute** total, rather than the minute to remove plus the minute to place, and neither bearer takes the damage that removal normally deals. You may do this during a short rest without the recipients losing the rest's benefit. The party's stolen powers become a shared kit, redistributed for the job at hand.
- **10th — Anchor.** You are the fixed point your gifts are keyed to. Creatures bearing your spikes have **advantage on saving throws against control** while within 60 feet of you, as your intent occupies the holes that something else would use. If you are Incapacitated, they lose this at once, and often notice.
- **14th — The Ministry's Whole Art.** Your intent sits in every spike you have placed the way an Allomancer's control does. Any creature attempting to control one of your bearers must first succeed on a check against your **Hemalurgy save DC**, as though wresting that control away from you, and **Anchor** now reaches every bearer whose location you know, at any distance. In addition, a creature bearing a spike you placed may, once per long rest, use its stolen power at **surge tier**, as though it had been flared with duralumin (see the core rules). You have made an order, and it can act like one.

---

{{imageMaskEdge6,--offset:10%,--rotation:270
  ![A Steel Inquisitor, by The Bestower](https://cdn.jsdelivr.net/gh/The-Architects727/MistbornDnD@85f0afc230a338f514f7d866b86aa0602ff0c0fe/final-render/art/hemalurgist-bestower-inquisitor.jpg?v=4d16e640){height:100%}
}}

\page
{{imgph imgphWide,style=min-height:64em
<!--h:112-->
**[ART: hema-bindpoints]** *THE BIND POINT DIAGRAM. A human figure with every known placement marked and labelled by metal and effect.*

**FULL** not supplied | ratio 0.77:1
}}

{{imgph,style=min-height:17em
<!--h:15-->
**[ART: hema-chimera]** *A Hemalurgic chimera: quadrupedal, canine-twisted, thick-skulled.*

**COLUMN** not supplied | ratio 1.33:1
}}

\page
{{partCover}}

# Part 5
## The Metal Economy

\page
## The Metal Economy

*Allomancy is the only magic in the world with a shopping list. A Coinshot out of steel is a man with a coin and an opinion.*

Every Metallic Art runs on metal you have to buy, carry, and eventually run out of. What follows is what metals cost, what forms they come in, how long a vial actually lasts, and what happens when somebody sells you a bad alloy.

> **The short version.** The eight common metals are effectively free and you should not track them closely. The four **enhancement** metals cost real money per use. The **god metals** cost more per charge than most parties see in a level. That spread is the whole economy.

---

{{tableGroup

### What you buy

Metal for burning is sold in three standard forms.

| Form | Weight | What it is |
|---|---|---|
| **Vial** | 5 g | Flakes or shavings suspended in alcohol. The standard carry, drunk in one swallow |
| **Powder** | 50 g | A pouch of ground metal, ten vials' worth. What you restock from |
| **Bead** | 2 g | A dense, pea-sized nugget. Discreet carry, high-value barter, and the raw form for a Hemalurgic spike |

}}

**Every vial holds the same five grams, whatever the metal.** Vials are sold by weight, so they differ in size rather than in dose. Five grams of aluminum is a generous pinch of flakes that clouds the whole vial; five grams of gold is a small bright dusting in the bottom of one. Aluminum takes up roughly seven times the room of gold for the same weight, and a bandolier of aluminum vials looks it.

Feruchemists buy the same metals in different shapes: **rings** (roughly 2 to 10 g), **bracers** (10 to 40 g), and **studs or spikes** for wearing under the skin. A metalmind is just metal, so it costs whatever that weight of that metal costs, plus the smith's fee.

---

{{tableGroup

### Prices

**Raw material cost** is what the metal itself is worth by weight. This is the honest number and it is what the three forms are priced from.

| Metal | Composition | Per gram | Vial (5 g) | Powder (50 g) | Bead (2 g) |
|---|---|---|---|---|---|
| **Iron** | Pure | 0.0002 gp | negligible | 1 cp | negligible |
| **Steel** | 98% iron, 2% carbon | 0.0006 gp | negligible | 3 cp | negligible |
| **Zinc** | Pure | 0.0008 gp | negligible | 4 cp | negligible |
| **Copper** | Pure | 0.0011 gp | 1 cp | 6 cp | negligible |
| **Pewter** | 91% tin, 9% lead | 0.0015 gp | 1 cp | 8 cp | negligible |
| **Brass** | 75% copper, 25% zinc | 0.002 gp | 1 cp | 1 sp | negligible |
| **Tin** | Pure | 0.002 gp | 1 cp | 1 sp | negligible |
| **Bronze** | 88% copper, 12% tin | 0.004 gp | 2 cp | 2 sp | 1 cp |
| **Cadmium** | Pure | 0.05 gp | 2 sp 5 cp | 2 gp 5 sp | 1 sp |
| **Bendalloy** | 50% bismuth, 26% lead, 14% tin, 10% cadmium | 0.06 gp | 3 sp | 3 gp | 1 sp 2 cp |
| **Electrum** | 45% gold, 55% silver | 0.08 gp | 4 sp | 4 gp | 1 sp 6 cp |
| **Gold** | Pure | 0.11 gp | 5 sp 5 cp | 5 gp 5 sp | 2 sp 2 cp |
| **Chromium** | Pure | 5 gp | 25 gp | 250 gp | 10 gp |
| **Duralumin** | 96% aluminum, 4% copper | 50 gp | 250 gp | 2,500 gp | 100 gp |
| **Nicrosil** | 85% tin, 15% chromium | 5 gp | 25 gp | 250 gp | 10 gp |
| **Aluminum** | Pure | 50 gp | 250 gp | 2,500 gp | 100 gp |
| **Malatium** | Atium and gold | 350 gp | 1,750 gp | 17,500 gp | 700 gp |
| **Atium** | Pure | 500 gp | 2,500 gp | 25,000 gp | 1,000 gp |

}}

\page
#### What you actually pay

Material cost is not shelf price. Somebody has to grind the metal fine, suspend it, and stake their reputation on the alloy being exact, and **a false alloy is worthless**, so that guarantee is most of what you are buying on the cheap metals.

- **A prepared vial of any common metal costs 1 gp**, whatever the table above says. You are paying for the work and the warranty, not the tin.
- **Buying by the pound** is how the common metals are actually traded, at the per-gram prices above. Bring your own mortar.
- **The expensive metals** are priced by material, so the table stands.
- **Aluminum is the difficulty, not the ore.** Bauxite is common and aluminum is the most abundant metal in the ground, but freeing it takes either electrolysis or a volcano, and a world without the first has only the second. That is why a pistol made of it buys a house and a carriage, and why a single vial costs more than most people see in a year. **Duralumin is 96% aluminum and priced accordingly.**
- **Chromium and nicrosil are merely difficult.** Dissolve the ore in hydrochloric acid, reduce it in a charcoal oven: an alchemist can do it, and some do, which is why they cost what a good horse costs rather than what a house does.
- **Prices double or worse** where a metal is scarce, controlled, or being sold to someone with no other option.

**Grind your own.** This gap is worth a player noticing. A pouch of tin **powder** holds ten vials' worth and costs **1 silver**; ten prepared **vials** of the same tin cost **10 gold**, a hundred times more. Buying powder and preparing your own vials takes about an hour, a mortar, and some strong spirits, and it is the single largest saving available to a working Allomancer. It also means you are trusting your own purity checks instead of somebody else's, which is exactly why the Alloyer feat pays for itself.

---

{{tableGroup

### What a vial buys you

This is the table that matters at play. A **vial is 5 grams**, and what that means depends entirely on the metal.

| Metal | Charges/g | Charges in a vial | Tempo | A vial at base burn | Cost per charge |
|---|---|---|---|---|---|
| **Tin** | 60 | 300 | Minute | 5 hours | negligible |
| **Pewter** | 50 | 250 | Round | 25 minutes | negligible |
| **Bendalloy** | 50 | 250 | Minute | 4 hr 10 min | negligible |
| **Copper** | 40 | 200 | Minute | 3 hr 20 min | negligible |
| **Bronze** | 30 | 150 | Minute | 2 hr 30 min | negligible |
| **Cadmium** | 30 | 150 | Minute | 2 hr 30 min | negligible |
| **Iron** | 20 | 100 | Minute | 1 hr 40 min | negligible |
| **Steel** | 20 | 100 | Minute | 1 hr 40 min | negligible |
| **Zinc** | 20 | 100 | Minute | 1 hr 40 min | negligible |
| **Brass** | 20 | 100 | Minute | 1 hr 40 min | negligible |
| **Gold** | 10 | 50 | Minute | 50 minutes | ~1 cp |
| **Electrum** | 10 | 50 | Minute | 50 minutes | ~1 cp |
| **Chromium** | 10 | 50 uses | Instant | 50 separate burns | **1 sp 5 cp** |
| **Duralumin** | 10 | 50 uses | Instant | 50 separate burns | **2 sp** |
| **Nicrosil** | 10 | 50 uses | Instant | 50 separate burns | **2 sp** |
| **Aluminum** | 10 | 50 uses | Instant | 50 separate burns | **2 sp 5 cp** |
| **Malatium** | 10 | 50 | Round | 5 minutes | **35 gp** |
| **Atium** | 10 | 50 | Round | 5 minutes | **50 gp** |

}}

**Read that last column.** A round of flared pewter costs a fraction of a copper piece. A round of atium costs fifty gold. That is not a rounding difference, it is the design: common metals are a non-issue you should hand-wave, and god metals are a resource the whole table feels.

**Flaring multiplies the cost.** Every figure above is base burn, one charge per tempo unit. A Coinshot flaring ten charges a round is spending eleven times as fast. On tin that is still nothing. On atium that is 550 gp a round.

---

\page
{{tableGroup

### Availability

Not everything is on a shelf. Roll these into whatever your setting already does with rare goods.

| Tier | Metals | Where |
|---|---|---|
| **Common** | Iron, steel, tin, pewter, zinc, brass, copper, bronze | Any town with a smith. Nobody asks why |
| **Uncommon** | Cadmium, bendalloy, gold, electrum | Cities, alchemists, and specialist suppliers |
| **Rare** | Chromium, nicrosil, duralumin | Capital cities and dedicated dealers. Expensive and remembered |
| **Restricted** | **Aluminum** | Controlled wherever anyone understands it. Buying quantity draws attention, and in many places it is outright illegal |
| **Legendary** | Atium, malatium, lerasium, trellium | Not sold. These are treasure, plot, and reward, placed by the DM and never stocked |

}}

**Why aluminum is watched.** It cannot be Pushed or Pulled, it shields a mind from emotional Allomancy, and burning it strips an Allomancer's reserves. Anyone who rules by Allomancy has an excellent reason to control who owns it, and historically they always have.

---

### Purity, and being cheated

**An alloy that is not exact does not work.** Ninety-one parts tin to nine parts lead is pewter. Ninety to ten is a lump of metal that will not burn, and an Allomancer who finds that out does so at the worst possible moment.

- Metal from a **reputable supplier** is good. Metal from anywhere else is a question.
- When buying from an unknown or disreputable source, the DM may call for a **Wisdom (Insight)** check against the seller, or simply decide. A bad batch typically burns at **half charges**, or does not burn at all.
- A character with the **Alloyer** origin feat is never fooled. They can determine any sample's exact composition in a minute and know instantly whether it will burn, which makes them extremely popular with people who buy metal in bulk.
- **Pure metals** (iron, tin, copper, zinc, cadmium, chromium, aluminum, gold) cannot be faked by ratio, only adulterated. **Alloys** are where the money is made and lost.

---

\column

### Carrying it

What you can carry is governed by the core rules, not by cost.

- You may swallow as much as reasonably fits, a generous soft limit with no hard gram cap.
- **Metal still unburned 24 hours after you swallow it causes metal poisoning.** Load up before a fight, not before a journey.
- Metal **worn or embedded** rather than swallowed is not on that clock, which is why serious Allomancers carry vials and serious Feruchemists wear rings.
- Coins are metal. A pouch of steel coins is a Coinshot's ammunition and a Hazekiller's reason to carry none.

---

### The god metals

Atium and malatium are priced above for completeness, because someone will eventually loot a bead and want to know what it is worth. **Lerasium** and **trellium** have no price at all; they are artifacts and campaign events.

Treat god metal as **economy and DM reward**, never inventory. A bead of atium is two grams, twenty charges, and twenty rounds of seeing the future. It is also a thousand gold pieces that somebody will kill you for.

{{imgph,style=min-height:17em
<!--h:15-->
**[ART: bloodlines-vial]** *A vial of metal flakes held up to lamplight, the shavings suspended in alcohol. Placed in the Metal Economy, beside what a vial costs.*

**COLUMN** not supplied | ratio 1.33:1
}}

{{imgph,style=min-height:17em
<!--h:15-->
**[ART: economy-forms]** *The three purchase forms side by side: vial, powder pouch, and bead.*

**COLUMN** not supplied | ratio 1.33:1
}}

\page
{{partCover}}

# Appendix
## The Arts and the Weave

\page
## The Metallic Arts and the Weave

*Rules for running Allomancy, Feruchemy, and Hemalurgy at an ordinary D&D table, in a world that also has spells, spell slots, magic items, and the Weave.*

Scadrial's Metallic Arts draw on **Investiture**, a different power source from the arcane and divine magic of a standard D&D world. This appendix defines how the two systems meet. The short version: **the wall is one-way.** Ordinary magic cannot reach the Metallic Arts, but the Metallic Arts, through a handful of specific metals, can reach ordinary magic, because to an Allomancer every power in the world reads as just another kind of Investiture.

### Principle 1: The one-way wall

Treat the **Metallic Arts** and the **Weave** (ordinary spells and magical effects) as separate power sources.

**Ordinary magic cannot affect the Metallic Arts.** An active burn is not a spell and does not register as one.

- **Counterspell** cannot stop a burn (nothing is being "cast").
- **Dispel magic** cannot end a time bubble, a soothe, a coppercloud, or any Allomantic or Feruchemical effect.
- **Antimagic field** does not suppress Allomancy or Feruchemy. A Mistborn standing in one keeps Pushing, flaring, and burning. *(Aluminum, not the Weave, is the cosmere's true antimagic.)*
- **Detect magic** and arcane divination do not reveal an Allomancer, their reserves, or their burns. To the Weave, Investiture is simply not there.

**The Metallic Arts can affect ordinary magic,** but only through the metals built to touch Investiture. Everything a metal can normally do to Allomancy, it can do to a spell or magical effect, treating that magic as the Investiture it fundamentally is:

| Metal | Reaches the Weave by |
|---|---|
| **Aluminum** | Cleansing spells and magical effects from **yourself** |
| **Chromium** (Leecher) | Draining active magic from **others** on touch |
| **Duralumin** | Bursting **your own** other-Investiture (a spell, a tap) in one instant |
| **Nicrosil** (Nicroburst) | Bursting or forcing **another's** magic on touch |
| **Bronze** (Seeker) | **Sensing** any use of magic nearby |
| **Copper** (Smoker) | **Hiding** those within its cloud from magical senses |

No other metal interacts with the Weave. A Coinshot cannot Push a *spiritual weapon* (it is not physical metal); a Rioter's emotional Allomancy works on a creature's feelings whether or not that creature casts spells, exactly as it always does.

### Principle 2: Internal versus external (the protection save)

When a metal **bursts, drains, or forces** a power, how firmly that power resists depends on **how much it is part of the wielder**. This single rule governs every interaction below.

- **External Investiture, no save.** An Allomancer's metal reserves are swallowed flakes, not part of the soul. Duralumin, nicrosil, and chromium take them wholesale. Only the *delivery* can be avoided: an unwilling, aware target of a chromium or nicrosil touch still gets a **Dexterity saving throw** to dodge the touch itself.
- **Internal Investiture, a saving throw.** Power drawn from the wielder's own spirit resists being torn out or forced. **Feruchemy** (drawn from your own attributes) and **D&D spellcasting** (spell slots are part of the caster) both grant the subject a **Constitution saving throw against the Allomancer's Allomantic save DC** to protect part of what would be taken. On a success, the subject **keeps half** (rounding in their favor) of the Investiture, slots, or charges that would otherwise be consumed or forced.

This is why a Nicroburst can rip an Allomancer's entire reserve out in a heartbeat but only *partly* force a wizard or a Feruchemist: the wizard's slots and the Feruchemist's stored self are theirs in a way a bead of steel never is.

### The bridging metals, formally

Each metal's own page carries its full rules; this section gives the Weave-specific detail. In every case the **charges you spend set the strength you can reach** (flare cap = your level), and a **savant** ignores that cap and can reach the very highest magic (a 9th-level spell, a legendary item, a Shard-touched effect).

#### Aluminum: cleanse yourself

Spend charges to end ongoing spells and magical effects **on yourself**, in addition to clearing your own metals. You may end one effect whose spell level (or a tier the DM sets for non-spell magic) is no greater than the charges spent. You choose to do this, so there is no save; it is your own spirit you are scouring. This covers curses, charms, ongoing concentration effects others have placed on you, and clinging foreign Investiture. A savant can burn out even a 9th-level or legendary effect. See aluminum.

\page
#### Chromium: drain active magic (touch)

On a touch (unwilling, aware targets get a Dexterity save to avoid it), end or suppress the target's **active magic**, choosing effects whose level is no greater than the charges spent:

- **End a concentration spell** the target is maintaining (this targets something part of them, so they make the Constitution protection save; on a success their concentration holds).
- **Snuff an active conjuration or ongoing effect** they are sustaining (a *spiritual weapon*, a *flaming sphere*, a summoned creature's tie to them).
- **Suppress a magic item** they hold or wear for 1 round (by item rarity as the level).
- **Dismiss a summoned or Invested weapon** for the round (a pact blade, a Shardblade, a *shadow blade*).
- **Drain foreign Investiture** clinging to them (borrowed Stormlight, a lodged Breath).

Chromium reaches only what is **live**. It never drains spell slots, prepared spells, or a creature's innate capacity to cast; the well remains, only the water in the air is gone. See chromium.

#### Duralumin: burst your own magic

When you flare duralumin, in addition to detonating your Allomantic metals, you may release **one non-Allomantic power you are using this turn** in a single, maximized instant:

- **A spell you cast this turn (or are concentrating on):** it is **maximized** (all its variable numbers taken at maximum). You may additionally feed in any number of your **remaining spell slots**; the spell is then treated as **upcast to the summed level of every slot consumed** (the casting slot plus all fed slots). A concentration spell burst this way goes off at this boosted power once, then ends. Because the slots are your own and willingly spent, there is no save. The flare cap limits nothing here except through your charges being spent on the detonation itself.
- **A Feruchemical tap:** the metalmind's draw is released in one amplified surge rather than over its normal duration, spending that portion of the mind at once.

This is the "one breath of power spent all at once," extended to every kind of Investiture you command. See duralumin.

#### Nicrosil: burst or force another's magic (touch)

On a touch (unwilling, aware targets get a Dexterity save to avoid it), do to a creature what duralumin does to you, with the internal-power save applying:

- **On a willing ally:** empower a spell they cast or a tap they make exactly as duralumin above, they choosing which slots to feed. A way to unleash your party wizard's nova on your action.
- **On an unwilling caster:** force them to **expend Investiture at the worst moment**. Their active spell or tap is triggered or wasted, and you may force them to burn additional spell slots. They make the **Constitution protection save**; on a success they keep half their slots (rounding in their favor) and the disruption is partial. Their Allomantic metals, if any, are taken with no save. This is resource denial, not a gift; you are making them blow their reserves. See nicrosil.

#### Bronze: sense magic

A Seeker burning bronze feels **any active use of Investiture** within range, and in a D&D world that includes ordinary magic. You feel a spell being cast, a magic item being used, a concentration effect being sustained, or a Feruchemist tapping, as a pulse whose direction, rough strength, and "rhythm" you can read, though you cannot name the exact spell. Dormant power is quiet: a wizard not casting, or a magic item sitting unused, gives little or nothing. A bronze savant, a double-bronze Twinborn, or duralumin-flared bronze reads more, and pierces copperclouds. See bronze.

#### Copper: hide from magic

A coppercloud hides the Investiture within it from being sensed. Against the Weave, **every creature inside** a coppercloud is hidden from **magical detection and divination**: *detect magic*, *scrying*, *locate creature*, and the like cannot find or read them while they remain inside, just as a Seeker's bronze cannot. The **Smoker** alone (not the others in the cloud, matching copper's emotional shield) additionally has **advantage on saving throws against divination and effects that would read or invade their mind**. The cloud's strength (the charges sustaining it) sets what level of magical senses it can defeat; only a bronze savant or duralumin-flared bronze can see through a strong one. See copper.

\page
### What the Metallic Arts ignore

Because a burn is an act of will on metal already inside you, not a spell, Allomancy sidesteps much of what stops a spellcaster. This is a real and deliberate advantage at a mixed table.

- **No components.** Allomancy has no verbal, somatic, or material components. **Silence** does not stop it, and being **grappled, restrained, or bound and gagged** does not: a captured Allomancer with metal in their stomach can still Push, soothe, or flare pewter. (This is why the Final Empire's prisons fed captives aluminum.)
- **Not a spell, so not counterable or dispellable,** as in Principle 1.
- **Concentration is separate.** Holding a time bubble or a sustained burn is not spellcaster Concentration; it is not broken by taking damage, and you can maintain it alongside a concentration spell if you also cast. Each metal page states what ends its effect.
- **The counters that remain** are the Investiture-aware ones: aluminum and chromium (rare, coveted metals), taking away or fouling an Allomancer's metal, and simply out-fighting them. A party facing an Allomancer should understand that the standard anti-caster toolkit largely does not apply.

\column

{{tableGroup

### Quick reference

| Situation | Ruling |
|---|---|
| Counterspell / dispel magic / antimagic field vs a burn | No effect |
| Detect magic vs an Allomancer | Reveals nothing |
| Silence / gagged / grappled Allomancer | Can still burn |
| Bronze (Seeker) near a spellcaster | Feels the casting (not the exact spell) |
| Coppercloud vs detect magic / scrying | Hides those inside; advantage vs mind-reading |
| Aluminum on yourself | End a spell/effect on you, level ≤ charges, no save |
| Chromium touch on a caster | End active effects (level ≤ charges); Con save on concentration; no slot drain |
| Duralumin on your own spell | Maximize + upcast to summed fed slots; concentration spell then ends; no save |
| Nicrosil on ally's spell | Same as duralumin, ally chooses slots |
| Nicrosil on enemy caster | Force wasteful expenditure; Con save protects half their slots |
| Any burst/drain vs Feruchemy or spell slots | Con save (internal power); vs Allomantic metal, no save |

}}