---
layout: post
title:  "MIT Mystery Hunt 2017 [Part 2/3]"
date:   2017-01-21 12:12:44 -0500
categories: mystery_hunt puzzlehunts
---

*This is part 2 of a series of posts about the MIT Mystery Hunt. You can find [part 1]({{ site.baseurl }}{% post_url 2017-01-20-mystery-hunt-2017-part-1 %}
) here.*

This post will attempt to address the two questions on everyone's minds right now: why was hunt so short, and is this a problem? First, the why.

Why was hunt so short? Well, it wasn't because there were too few puzzles or metas:

```
                | 2015      | 2016    | 2017
----------------+-----------+---------+----------------
 "easy" puzzles | 57 (fish) | 0       | 67 (character)
  total puzzles | ~160      | ~160    | ~160
          metas | 12 - 15   | 12 - 21 | 15
```

This year's hunt had close to 160 total puzzles and 15 metas, about the same as the numbers for prior years. It's not clear what exactly counts as a meta because of subtleties such as [meta-metas](http://web.mit.edu/puzzle/www/2015/puzzle/ocean_meta_meta/), [puzzles that reference other puzzles](http://web.mit.edu/puzzle/www/2015/puzzle/dory/), and [puzzlehunts within puzzlehunts](http://huntception.com/round/dreamtime/), but it's safe to say that the hunt wouldn't have been significantly longer had Setec simply included a couple additional character metas.

If it wasn't the number of puzzles, it must be their difficulty, right? Puzzles that appeared in the character metas were meant to be easier than average, an intentional throwback to the 2015 hunt which included "fish" puzzles designed to be about 1/3 the difficulty of a normal Mystery Hunt puzzle. However, the number of fish puzzles and character puzzles was roughly the same, and the hunt had plenty of difficult puzzles.

The problem wasn't so much a lack of hard puzzles as a misassignment of puzzles to metas which often had too much flavortext and lent themselves too easily to backsolving. In Random's 2015 hunt, all the fish puzzles comprised [one (very large) meta](http://web.mit.edu/puzzle/www/2015/puzzle/school_of_fish_meta/), leaving the other 11ish metas filled which much more difficult puzzles. (In particular, the final four [tower metas](http://web.mit.edu/puzzle/www/2015/puzzle/colorful_tower_meta/) had much *harder* puzzles than average, and took a lot longer to crack). In this year's hunt, the easy puzzles were distributed among 6 different character metas which were themselves very straightforward.

Although the puzzles in the quest metas were generally harder, there were often enough easy puzzles that could be solved to crack the meta. The truly hard puzzles were either backsolved or just ignored completely as they didn't increase the characters' levels. The quest metas themselves were nice and involved some clever constructions, but these were often undermined by too much flavortext which pointed towards the correct approach too quickly.

As an example, consider the [Thrilling Thespians](http://solutions.monsters-et-manus.com/hunt/round/thespians.html) meta. Solvers were given 10 puzzles divided between "Stage Left" and "Stage Right." The flavortext mentioned Shakespeare and specific individuals in his plays. The solution involved pairing answers from Stage Left and Stage Right and adding a letter in between the two answers to produce a main character in one of Shakespeare's works. Sorting by the starting and ending letters of the two puzzle answers produced I AM BI, the meta answer:


```
Stage Left  | Character  | Stage Right
------------+------------+-----------
ALLEGORICAL | CAL I BAN  | BANANARAMA
    BISTROS | ROS A LIND | LINDEN LAB
    CAPTCHA | HA  M LET  | LETHARGIC
DWARF SUMAC | MAC B ETH  | ETHELRED
 EMAIL SCAM | CAM I LLO  | LLOYD GEORGE
```

This is a cute idea for a metapuzzle, but it's far too easy as written. By the time my team had about half the puzzle answers we had figured out pretty much exactly what to do, and with a few more puzzles solved we were able to submit the correct answer.

There are a number of things that could have been done to make this meta more difficult. First, why bother providing solvers the division between Stage Right and Stage Left? It's perfectly reasonable to simply mix all the puzzles together and expect solvers to determine the pairing themselves. The Stage Left puzzles all begin with A - E and the Stage Right puzzles end with A - E, so this would serve as further confirmation that pairing is the right thing to do.

Second, why even mention Shakespeare in the flavortext? Shakespeare is sufficiently important to the theater that solvers can be expected to make the connection on their own. It's a lot more satisfying to figure out for yourself that the puzzle involves constructing Shakespearean characters than it is to have the flavortext simply tell you to do so.

Contrast this meta with the [Randolph Carter](http://huntception.com/round/randolph_carter/) round in the 2016 hunt. In that meta, all the answers shared a word with a *Nightmare on Elm Street* film title, but in that case the only reference towards the films was an oblique use of the word "nightmare" in the flavortext. I was the one who figured this out on our team last year, and it was incredibly exciting to know that my insight cracked an entire meta. This sense of discovery is robbed from solvers when the flavortext is too helpful.

The final issue with the metas is that the puzzles inside them were too easily backsolved once the meta was completed. In two of them (the [Cleric](http://solutions.monsters-et-manus.com/hunt/round/cleric.html) and [Chemist](http://solutions.monsters-et-manus.com/hunt/round/chemist.html) metas), after solvers determined the meta answer, they essentially could backsolve every single remaining puzzle in the round. This isn't in and of itself a major problem. In fact, it looks like our team backsolved proportionally about as many puzzles in 2016 as in this year (13 and 16 respectively). This became a larger problem when the puzzles in the quest meta rounds varied in difficulty. In many instances, we were able to skate by, solving only the easy puzzles and skipping the harder ones designed to slow us down.

Furthermore, solving a quest meta had the effect of raising every character's level which then unlocked even more puzzles, creating a feedback loop. At one point we had 3 quest metas all open with zero solves among them. A team as large as ours had the manpower to deal with so many open puzzles, (and this was doubly true with even larger teams like Death and Mayhem and Palindrome) but smaller teams could easily become overwhelmed.

All of this led to a much shorter hunt experience than usual. I went to sleep at around 4:00 AM on Saturday, just after we got the email that Death and Mayhem had found the coin. By the time I woke up at 9:00, our team had solved all the metas except one, which fell soon afterwards. (Incidentally, [that meta](http://solutions.monsters-et-manus.com/hunt/round/minstrels.html) contained one of the few errors in this year's hunt, which delayed us by a fair amount. Somehow the three teams in front of us managed to solve it despite the error and without alerting HQ of the issue.)

Now, a few points on the more difficult question: is this a problem? Let's first make one thing clear: Setec never intended or expected the hunt to be this short. Because of level constraints, the endgame was only meant to be accessible to teams that had completed all 5 events, the last 3 of which hadn't yet happened by the time Death and Mayhem finished all the metas. Setec coped well with this situation, hosting private versions of the events early for teams that were ready to go on the runaround, but as they explained at wrap-up, they intended for the winning team to find the coin early Sunday morning—about 24 hours *after* when it was actually found.

The shorter hunt gave a lot of smaller or less-experienced team the opportunity to make much more progress than in previous years. Setec mentioned at wrap-up that a record 17 teams finished the entire hunt, and another 29 solved all the character metas. This leads to the question: how do you design a hunt experience that is fun for teams of all sizes and skill levels?

I don't think the answer is to plan for a hunt to last only 14 hours for the winning team. In fact, based on the design of this and past hunts, I think that we've already solved this problem in theory (if not in practice). The solution is to carve out a portion of the hunt that is relatively self-contained which contains puzzles accessible to novice solvers. For Setec, this was meant to be the six character metas, for the Sages it was [Round 0](http://www.mit.edu/~puzzle/2013/enigmavalley.com/), and for Random it was the [school of fish meta]((http://web.mit.edu/puzzle/www/2015/puzzle/school_of_fish_meta/)).

In the end, I think this is an issue where there is actually a lot less disagreement than blog posts about the hunt would indicate. Basically I think almost all serious or semi-serious hunters would be relatively happy with a hunt where:
* the coin was found sometime early Sunday
* smaller teams could make steady progress towards a major "objective"
* somewhere between 4 - 14 other teams get to complete the runaround

The problem isn't agreeing on these goals: it's accomplishing them. Events on the scale of the Mystery Hunt are wild, unpredictable beasts. Ultimately, writing teams need to set reasonable goals, make back-up plans, and hope for the best.

*You can find my final post on the hunt [here]({{ site.baseurl }}{% post_url 2017-01-22-mystery-hunt-2017-part-3 %}).*
