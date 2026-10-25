# TakeMeter

> ### 👋 Start here
>
> **New to this repo? Read [RUNNING.md](RUNNING.md) first** — setup, the
> notebook, the baseline, and what to do when something breaks.
>
> Once `python test.py` passes:
>
> ```bash
> head -5 data/practice_labels.csv     # the shape your labels.csv needs
> ```
>
> Then open `takemeter.ipynb` **in this folder** — in VS Code, or with
> `jupyter notebook` if you prefer. Pick the kernel: the `.venv` inside this
> project. Run section 1, which reports the hardware you'll be training on.
> Everything else waits until you have data.
>
> Nothing to upload, nothing to connect, no accounts and no keys. The notebook
> runs on your machine and writes next to your code.
>
> **The rest of this file is your submission.** Fill it in as you go.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     HOW TO USE THIS FILE

     Unit 5 asks for the first five sections. Unit 6 adds the five below them.

     Everything is pasted as TEXT. No screenshots, no images.

     ⚠️ The confusion matrix especially. The notebook prints one as a markdown
     table, ready to copy. A screenshot of a matrix earns nothing. Paste the
     table.
     ───────────────────────────────────────────────────────────────────────── -->

<!-- ═══════════════════════ UNIT 5 — THE BUILD ═══════════════════════ -->

## What This Does

<!-- Your community, and what your classifier sorts posts into. Three or four
     sentences. -->

This is a text classifier for posts in r/GenshinImpact on Reddit. Posts are sorted into `theorycrafting`, `lore`, and `game_mechanics`. `theorycrafting` is for posts surrounding team composition, character damage output, or character building. `lore` is for posts discussing game lore and predicting future events based off that; `game_mechanics` is for discussion surrounding puzzles, materials, map exploration, etc.


---

## Label Taxonomy

<!-- Each label: a one-sentence definition and two real examples from your
     reading. Then your decision rule for the hardest boundary.

     The decision rule is worth a point on its own and it's the thing most
     people leave out. Every taxonomy has a hardest boundary. Name yours. -->

### `lore`

**Definition:**
This is a post discussing background lore of in game content. 

**Example 1:**
> [Personally, I've recently been looking a lot into Zongli's lore, because i think he just knows too many secrets.](https://www.reddit.com/r/Genshin_Impact/s/kRyIoFvOsf)

**Example 2:**
> [ Would the Hexenzirkel protect Rhinedottir?: I've been thinking about this since finishing the latest archon quest. If Rhinedottir found herself in a similar situation to Ronova, that being vulnerable and about to be killed. Either by the fatui, Dainsleif or even the Traveler, would Alice and the other witches intervene to save her? It really surprised that Rhinedottir even after becoming a shade still sees herself as Mage R, which probably means that she still considers herself a Hexenzirkel witch. Also despite the other witches rarely talking about her, from what they have said they definitely still see her as a friend and member of the group. Alice especially doesn't seem like someone who would ignore a close friend in a dire situation. I personally think if Rhinedottir was about to be struck down that Alice would appear and save her. But I also don't think that Rhinedottir would ever let herself be put in that position, she's way more likely to just betray the Heavenly Principles and side with the Tsaritsa if given the opportunity.](https://www.reddit.com/r/Genshin_Impact/s/XOaaghANCE)

### `theorycrafting`

**Definition:**
These are posts discussing character kit design, how to build teams or characters, or maximize damage output from characters. 

**Example 1:**
> [Struggling to decide if I should get Escoffier: I’m a Wriothesley main and have been for some time now. I mostly play him in Freeze teams and so naturally Escoffier would be an upgrade for that. My current team is C1R0 Wriothesley/C0R1 Furina/C0R0 Vodyanitsa/C0R0 Xilonen, and I do get good numbers with it. My problem arises from the fact that I don’t like to spend too much (usually only the Welkin) and that there might be characters getting reruns in the near future that I want. I’m not that fussed about Escoffier’s character; if I were to pull her it would be purely for utility. So I suppose my question is; is she enough of an upgrade to warrant pulling her or not? Also, I should probably mention that I don’t have Skirk and am not interested in getting her, so she wouldn’t have any value there.](https://www.reddit.com/r/Genshin_Impact/s/DUKU17FFVA)

**Example 2:**
> [what's the best rotation for vesna c1?: team is c1 vesna, c0 odette, c2 vodyanitsa, c6 faruzan i already have a rotation figured out for odette, vodyanitsa, and faruzan, but i'll try out any rotation suggestions i can't really find any rotations that increase my damage at all, and i'm mainly looking for rotations that will work at full power 2 rotations in a row, because some rotations i've found are really fast and don't give faruzan's burst enough time to recharge also have a nice day everyone, and i wish you all the luck i had of 6 50/50s won in a row with avg 40 pity](https://www.reddit.com/r/Genshin_Impact/s/szfoJsNVRM)

### `game_mechanics`

**Definition:**
These posts discuss in game mechanics, such as puzzles, materials collection, map exploration, etc.

**Example 1:**
> [How rare are these drops?: The first image was 40 resin (double) and the second image was a transient (60) resin (triple) How rare is it for these to be the drops for each respectively? I’m just curious if they are pretty uncommon or I’m just unlucky to not see these drop as I usually get a couple blues and greens and the occasional purple.](https://www.reddit.com/r/Genshin_Impact/s/WqsJSk45xC)

**Example 2:**
> [Primo farm: Guys how do you farm for primos after completing almost whole map as f2p player?? I genuinely dont know what to do anymore atp(all of my sub areas are 100% as well). I know theres more to farm even after getting it to 100% from hidden chest but im too lazy to watch tutorials rn.](https://www.reddit.com/r/Genshin_Impact/s/lQHRHZl336)

### The hardest boundary

**Which two labels:**
I expect `theorycrafting` and `game_mechanics` to be mixed up between the two. Certain in game puzzles may require specific team compositions to solve them, which may sound a lot like `theorycrafting`, which is instead aimed at maximizing damage output. 

**The decision rule I used every time:**
<!-- e.g. "If the post names a specific checkable fact, it's `analysis`, even
     if the tone is heated." -->

If the post names a specific in-game puzzle not related to endgame content (Spiral Abyss, Imaginarium Theater, Stygian Onslaught), the post is considered `game_mechanics`. Otherwise, the post is considered `theorycrafting`.

---

## The Dataset

<!-- Where you collected from, how you labelled, your counts, and three hard
     cases. -->

**Where the posts came from:**

Posts were selected from r/GenshinImpact on Reddit. 

**How I labelled them:** 
<!-- Cold first? Pre-labelled with AI and corrected?
Say so plainly — the disclosure is required, not penalised. -->

I just labeled them all myself. The hard part was finding 200 posts and formatting them correctly. Moving the `.csv` to a spreadsheet halfway helped with formatting. Labeling was fairly straightforward from that point. 

**Counts per label:**

| Label | Count | Share |
|---|---|---|
| `theorycrafting` | 94 | 47% |
| `game_mechanics` | 67 | 33.5% |
| `lore` | 39 | 19.5% |
| **Total** |  | 100% |

**Three hard cases**

<!-- Any post that made you pause: what it was, which two labels it could have
     been, and what you chose. These are worth more than the easy 190. -->

**1.**
> *The post:*
>
> [ catching up and *wow* moongazer  i fell behind after natlan, just too much real life. kept saying "i should catch up" for nearly 2 years and the 5* selector finally put the last wedge in the door for me to get back in, did all of nodkrai (also a fantastic binge), character story quests, permanent events, and then this quest. and what a quest, i felt like a little kid again, it was pure magic the whole way through. whoever decided genshin was going to the moon this summer deserves a raise alongside the background architects and composers. i don't know how it is for the average player, but i've always found the theme of sending messages through space so existentially romantic, the warm idea that you want another species smart enough to understand the size of the universe and how "lonely" any given planet or species really is to know that they aren't actually alone (let's just ignore the "oh btw there's a darkness devouring the galaxy gl hf" bit for a sec). AND THE SIBLING LORE AT THE END?!?!?! i would've never expected that out of HYV's big 3 games genshin would be the one to give me the best ship launch sequence, to showcase the vastness of space, to have a low-grav surface impact, to play with 4 levels of gravity, to scratch that scifi itch that so few games do... i did however, expect them to bring me yet another mascot character overflowing with selfless noble purpose, they're really good at that one... anyways i don't really have an essay or anything just wanted to make a little message of appreciation for an amazing night. i hope everyone else found this quest and area at least half as magical as i did. you are not alone 👍](https://www.reddit.com/r/Genshin_Impact/s/KE93dWoOBx)
>
> *Could have been:* 
>`game_mechanics`. There are a few lines discussing in-game mechanics (background music, design, unique movement environments).
>
> *I chose, because:* `lore`. The overall focus of this post is appreciation for this questline and the lore/background context around it.

**2.**
> *The post:* 
>
> [Two unrelated questions: 1. In nod krai there are little black speech bubbles with an exclamation point, what are they? I did one and got a chest, but others like the sugar sculpture seller don't seem to do anything. Am I missing something? 2. When should I do the zibai and Sandrone event/story quests? I skipped nod krai story for the free 5*, and don't want to accidentally spoil myself (any more) if it's possible to play them too early.](https://www.reddit.com/r/Genshin_Impact/comments/1x85isp/comment/phg1y60)
>
> *Could have been:* `lore`. The second question refers to some quest material that would be classified under lore.
>
> *I chose, because:* `game_mechanics`. The first question discusses in game puzzles. The second question comes about as a consequence of a game mechanic, but this is ultimately classified based on the first question.

**3.**
> *The post:* 
>
> [The global Buffs from Theater and SO  Do the global buffs from Theater and SO affect my characters also in Milliastra? in Dummy test? The oens tha buffs PS%, ATK% DEF% by 20% and the SO ones? Sometimes in the Dummy test I reach a score, the after sometimes (day or weeks), I reach a different score (10k of difference sometimes). Obviously I do at least 3 run each test, and I check if I changed Builds/piece on my characters.](https://www.reddit.com/r/Genshin_Impact/s/UETjn7QKKU)
>
> *Could have been:* `theorycrafting`. The post discusses buffs from endgame battle content.
>
> *I chose, because:* `game_mechanics`. The post is ultimately asking if the bonuses from endgame content carry over into other material in game, making it a post about game mechanics, not improving damage or building teams.

---

## The Training Run

<!-- Your starting model, your settings, and anything you changed and why. -->

**Base model:**
distilbert-base-uncased

**Settings:** <!-- epochs, learning rate, batch size, seed -->
EPOCHS = 3
LEARNING_RATE = 2e-5
BATCH_SIZE = 16

**Anything I changed from the defaults, and why:**

I did not change anything.

**Split sizes:** <!-- train / val / test, and per-label counts in the test
split. If a label had fewer than about 8 in test, say so — it explains a lot
of next unit's variance. -->

train 139, val 31, test 30

|label        |    train | val | test|
|---|---|---|---|
|lore         |      27  |  6  |   6|
|theorycrafting  |   65  | 15  |  14|
|game_mechanics   |  47  | 10  |  10|

[note] 'lore' has only 6 examples in the test split.

A metric computed on that few examples moves a lot between seeds.
Write that down now — next unit it's a diagnosis, not a surprise.

**Above taken from *Section 3. Split* output.**


---

## How I Used AI

<!-- Two specific moments — what you asked, what came back, what you changed.

     ⚠️ Plus disclosure of any pre-labelling. If you had a model pre-label a
     batch and then read and corrected every one, say that. It's an allowed
     workflow and disclosing it costs you nothing. Not disclosing it is the
     problem. -->

**Moment 1**

- *What I asked for:* I used AI for feedback on my labels as suggested in the guidelines (create posts that might span two labels).
- *What came back:* The AI created several posts that might sit on the boundary of two labels.
- *What I changed:* I rephrased some of the label definitions and thought about what I had or hadn't considered part of some label. I edited my label definitions to better accomodate and differentiate between posts. 

**Moment 2**

- *What I asked for:* I used the AI to push back against my criteria. 
- *What came back:* The AI pointed out which criteria might be easily passed and which might be impossible.
- *What I changed:* I changed the wording and reasoning on some of the criteria to better explain the logic behind them. I also took into consideration how certain scoring criteria worked with finetuned models, and made adjustments based off that. 

**Pre-labelling disclosure:**

I did not prelabel anything with an AI tool. It was more convenient for me to label posts when working with them as a spreadsheet.

**Moment 3**

- *What I asked for:* I used the AI to discuss the case when I disagreed with the staff labeling. 
- *What came back:* The AI gave arguments for each label.
- *What I changed:* I did not end up changing my decisions. The feedback from the AI was mostly about how I defined "an argument backed by a specific, checkable fact". I maintain that the facts and conclusion have to be tied together to form a cohesive argument regardless of how inflammatory the argument sounds.

<!-- ═══════════════════════ UNIT 6 — THE TEST ═══════════════════════

     Don't fill these in during unit 5.
     ═══════════════════════════════════════════════════════════════════ -->

---

## Baseline vs. Trained

<!-- Both models on the same posts. `python baseline.py --trained results.json`
     prints this table for you. -->

| Measure | Baseline | Trained | Difference |
|---|---|---|---|
| Overall accuracy | 0.300 | 0.467 | +0.167 |
| Macro F1 | 0.275 | 0.212 | -0.063 |
| F1 — `game_mechanics` | 0.462 | 0.000 | -0.462 |
| F1 — `lore` | 0.364 | 0.000 | -0.364 |
| F1 — `theorycrafting` | 0.000 | 0.636 | +0.636 |

**What I predicted before I looked:**
<!-- Milestone 1 asks you to write this BEFORE seeing the trained numbers. A
     prediction made afterwards isn't one. -->
     
I believe my trained model will perform better in the `theorycrafting` label, as this is where the language used becomes more specific to the corpus community.

**What the gap actually means:**
<!-- If the baseline matched your trained model, your fine-tuning added
     nothing — and that is a real finding, not a failure. Say it plainly. -->

The overall accuracy improved a little from what you'd expect from random guessing, indicating that something was learned during the previous training, if minimally. The F1 score on my predicted label `theorycrafting` did improve, while the F1 score for my other labels got worse (to 0). An F1 score of 0 for those labels tells me that there were no True Positives in my test dataset. 

---

## Run Log — Before

<!-- Five criteria across three seeds. The notebook's section 6 prints the
     spread table; the Target and Verdict columns are yours. -->

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

| Measure | Seed 42 | Seed 7 | Seed 2024 | Spread |
|---|---|---|---|---|
| Overall accuracy | 0.467 | 0.467 | 0.467 | 0.000 |
| Macro F1 | 0.212 | 0.212 | 0.212 | 0.000 |
| F1 — `lore` | 0.000 | 0.000 | 0.000 | 0.000 |
| F1 — `theorycrafting` | 0.636 | 0.636 | 0.636 | 0.000 |
| F1 — `game_mechanics` | 0.000 | 0.000 | 0.000 | 0.000 |

This is suspiciously stable. 


### Confusion matrix

<!-- ⚠️ TYPED AS A MARKDOWN TABLE. The notebook prints one ready to paste.
     An image of a matrix earns nothing. -->

| true \ predicted | lore | theorycrafting | game_mechanics |
|---|---|---|---|
| **lore** | 0 | 6 | 0 |
| **theorycrafting** | 0 | 14 | 0 |
| **game_mechanics** | 0 | 10 | 0 |

**My biggest off-diagonal number, and what it means:**
<!-- Not "the model made mistakes" — WHICH boundary it didn't learn, and which
     direction. "7 real analysis posts were called hot_take and only 3 went the
     other way" is a direction, not just an error rate. -->

This is overall abysmal, but the largest mistake comes from 10 `game_mechanics` posts being labeled `theorycrafting`. Overall, it seems like everything is being labled `theorycrafting`. The model, seemingly, is just labeling every post the most common label. It seems nothing was learned except the average (mode) label.


---

## Verdicts and Diagnoses

<!-- MET or MISSED against LAST UNIT's target. The target has to hold across
     all three seeds, not turn up sometimes. -->

| # | Criterion | Target | Verdict | How I decided |
|---|---|---|---|---|
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
| 4 |  |  |  |  |
| 5 |  |  |  |  |

**Diagnoses**

<!-- For each miss: the cause, and how you know. The four common causes are:
     too few examples for a label, a boundary you applied inconsistently, a
     genuinely hard label pair, and a task the model can't reach from this
     much data.

     ⚠️ Use your agreement report as evidence. It is the only instrument you
     have that can tell a LABELLING problem from a MODEL problem, and this
     section is graded on whether you used it that way. -->



---

## Agreement Report

<!-- Your rate against the staff set, and every disagreement adjudicated.

     Remember you labelled these 30 under the STAFF taxonomy in
     data/staff_taxonomy.md, not your own — so every argument below is made
     from those definitions and those decision rules. -->

**Agreement rate:** 26 / 30 = 87%

<!-- Nobody grades this number. A 60% who argues every disagreement from the
     stated rules beats a 95% who wrote "staff was right" nine times. Several
     of the 30 were chosen because they're genuinely ambiguous — you should be
     winning some of these. -->

**Disagreements**

<!-- Three lines each: the post, both labels, and who you think is right and
     why — grounded in the staff definitions you were both applying.

     Then sort each into one of three piles:
       (a) the rule covered it and I applied it loosely → a consistency problem
       (b) the rule genuinely doesn't say               → a gap in the definitions
       (c) the rule is ambiguous here and my reading is defensible → argue it.
           This is a legitimate win.

     Pile (a) is the one that matters most for your diagnosis: if you applied a
     written rule two different ways on 30 posts, that is direct evidence about
     what you did across your own 200. -->

**1.**
> *The post:*
> The club championship scoring changed in 2019 from top-6 to top-10. Since then our B team has finished above the A team twice. That's not depth improving, it's the scoring rewarding turnout.
> *Staff said / I said:*
> `analysis` / `hot_take`
> *My call, and why:*
> I thought this to be a `hot_take` since there didn't seem to be any analysis or argument that the facts were doing. It felt like two separate facts and I am unclear what the conclusion or final argument is.
> *Which pile:*
> I believe this belongs in Pile (c). `analysis` says that an argument has to be backed with specific facts. I do not agree that an argument backed by facts was made. The final claim, if you consider it one, isn't supported by facts, which would make it a `hot_take`.

**2.**
> *The post:*
> Three of us ran the same session on the same day, different shoes, within 10 seconds of each other over 5 miles. I'm not saying shoes do nothing, but whatever they do was smaller than the noise between three people.
> *Staff said / I said:*
> `analysis` / `hot_take`
> *My call, and why:*
> This should be an `analysis` post. There are facts backing up an implied argument, that the shoes are don't do anything.
> *Which pile:*
> This is Pile (a), the rule did cover it.

**3.**
> *The post:*
> Times are down about 3% since the shoe rules changed, so obviously the shoes are the whole story and the sport has a problem.
> *Staff said / I said:*
> `hot_take` / `analysis`
> *My call, and why:*
> I think this is `analysis`. The argument gains the tone of an unbased claim with "so obviously", but this doesn't change the fact that there was a fact attached. The resulting conclusion might be dubious, but it's still some analysis, albeit a poor one. 
> *Which pile:*
> Pile (c), there is a stated fact backing an argument, even if the argument is written to be combative and frames someone disagreeing as foolish.

**4.**
> *The post:*
> Every injury thread on this forum is the same injury and the same three replies.
> *Staff said / I said:*
> `hot_take` / `reaction`
> *My call, and why:*
> I think this still belongs in `reaction`, as it is reacting to the contents of the forum.
> *Which pile:*
> Pile (c). To a reader, this post is clearly reacting to the contents of the forum. `hot_takes`, as unsupported claims, can also be a response to something, a `reaction`, so it is a little unclear. 

**What the pattern in my disagreements tells me:**

I seem to have a different standard for what constitutes a properly backed claim/argument. This matters in this taxonomy labeling, where what defines a well argued claim matters. This does not matter as much in my own corpus labeling, where the content of the post is more important than the manner in which it is delivered.


---

## The Improvement

**What I changed:**

**Which diagnosis pointed at it:**

### Run Log — After

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

**Did it help, and how do I know:**

<!-- If it didn't, say so. Relabelling that didn't help is a genuinely
     interesting result and earns full credit. -->



---

## What's Still Broken

<!-- For each criterion still missed: what you'd do, and why you stopped. -->



**The gap between what I meant my labels to capture and what the model
learned:**
<!-- Two sentences. Your confusion matrix is the evidence. -->



<!-- ═════════════════════════════════════════════════════════════════════

     SUBMISSION CHECKLIST — unit 5

       [ ] criteria.md has five numbered criteria, each naming a NUMBER
       [ ] Each has a reason underneath tied to your data or taxonomy
       [ ] labels.csv: at least 150 rows, text/label/note, ONE file not split
       [ ] No label above 70%
       [ ] All five unit 5 sections have real content
       [ ] Label Taxonomy includes the decision rule for your hardest boundary
       [ ] The Dataset includes three hard cases
       [ ] results.json and test_split.csv committed (the notebook does this)
       [ ] At least four new commits
       [ ] Repository URL submitted — WRITE IT DOWN

     SUBMISSION CHECKLIST — unit 6

       [ ] Baseline vs. Trained table, with your prediction written beforehand
       [ ] Run Log — Before, five criteria across three seeds
       [ ] Confusion matrix TYPED AS A MARKDOWN TABLE
       [ ] A verdict on every criterion
       [ ] A diagnosis for every miss, using the agreement report as evidence
       [ ] Agreement Report with every disagreement adjudicated
       [ ] One improvement, with Run Log — After
       [ ] What's Still Broken
       [ ] results_three_seeds_before.json, results_three_seeds_after.json,
           baseline_results.json and
           agreement_results.json committed
       [ ] At least four new commits
       [ ] The SAME repository URL as last unit

     Do not delete and recreate this repository.
     ═════════════════════════════════════════════════════════════════════ -->

---

📖 **How to run this project: [RUNNING.md](RUNNING.md)**
