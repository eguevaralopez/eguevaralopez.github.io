---
layout:      post
title:       "my quirky 440BX PC, p.1"
date:        2026-02-24 18:25:13 -0600
categories:  post
katex:      true
---
I have incredibly fond memories of my childhood PCs.

The first PC I remember owning (my parents bought it for me when I was entering highschool) was based around a **Pentium MMX 200**--it was the first computer I pulled apart and put back together by myself. I remember playing **Final Fantasy VII** on it at a snails-pace because I didn't have a proper 3D accelerator, what was in there was a [SiS6326](https://en.wikipedia.org/wiki/SiS_6326). I used it for homework, **Full Throttle**, and dial-up Internet.

It was amazing.

Of course the following year it was "obsoleted" by the **Pentium II**. I pushed hard for an upgrade but my parents, being wise, always said no. That is until my dad read an article in a PC magazine about the **Celeron 300A** and how easy it was to clock it up to 450 MHz. My dad, being a coscientiuos buyer, figured a budget Celeron-based PC would be more than enough for my needs, and trying to teach me something he handed me the magazine article and let me dig into how to make my Celeron go faster.

If he only knew that in 2026 I'd *still* be thinking about that PC. In fact I've made several attempts over the years at building a PC around my old Celeron 300A, its been almost a decade since my first effort--which [derailed very quickly](https://www.vogons.org/viewtopic.php?t=53839). There have been other attempts between then and now, but none successful.

After finding my Celeron 300A in a recent decluttering campaign, I'm once again inclined to attempt a build around it. I got rid of a lot of retro hardware I had accumulated over the years and kept only a handful of motherboards to play with, all of them from around the turn of the century--the time period of my highschool years. In no particular order,
- Intel VC820
- Intel OR840
- Intel D850EMV2
- Soyo SY-D6IBA
- and the subject of this post...
{:refdef: style="text-align: center;"}
![](/assets/img/2026-02-24-440bx_1.jpg){:width="90%"}
{: refdef}
{:refdef: style="text-align: right;"}
...the **PCPartner BXAS13-948C**
{: refdef}

### some detective work

I don't even remember what I was looking for when I stumbled upon this motherboard in ebay, but the twin Slot1/Socket370 config looked funky enough for me to click on the add. It was listed as *"ATA-N400-CX0 Dual Socket 370 & Slot 1 Motherboard Free Shipping"*, but after some googling of the model number I couldn't find much info about the maker.

Back in the day I did see a **PCChips** board with a similar config, but it was based on a SiS chipset. I had never seen such a config with what seemed to be an Intel chipset, which is what stroke me as curious. It also had 3 RAM slots and 2 ISA slots, which together hinted at it being based on the **i440BX**[^1].

I bit the bullet and bought it, and fair enough it had the i440BX chipset :) It was quickly [pointed out by the Vogons community](https://www.vogons.org/viewtopic.php?p=1338523#p1338523) that the VRM, an **LM2637M**, supported **Pentium*!!!*** CPUs; and the clock generator turned out to be a [Cypress W144H](https://www.alldatasheet.com/datasheet-pdf/view/227233/CYPRESS/W144H.html), capable of up to 150 MHz FSB. All in all a very capable combination, and it booted every Slot 1 CPU I threw at it: from a Celeron 300A, up to a Pentium*!!!* 1000B.

A quick search in theretroweb.com also allowed me to visually identify it as the [PCPartner BXAS13-948C](https://theretroweb.com/motherboards/s/pcpartner-bxas13-948c-bxas13-c948-35-c948). The documents available there[^2] reveal that this motherboard layout can accommodate various chipsets, including an **Apollo Pro133**. That chipset has official support for 133 MHz FSB, so the motherboard has proper ratios when using a 133 MHz FSB CPU, that is, the PCI/AGP buses will not be overclocked!

An i440BX motherboard with proper support for 133 MHz FSB CPUs is something I didn't expect to find in a cheap motherboard with a twin socket configuration!

The User Manual shows a table for the available multipliers of the board. I noticed a couple of interesting things--useless but interesting:
{:refdef: style="text-align: center;"}
![](/assets/img/2026-02-24-440bx_2.png){:width="70%"}
{: refdef}
- The 3rd jumper from left to right is always open for halves, you just take the previous integer and open the jumper.
- Jumper configurations for integer multipliers are formed by substracting 2 and converting to binary, but the order of the bits is not the usual 2,1,0; instead its the permutation 1,0,2 (excluding the 3rd jumper which is for halves). For example 3: 3-1 = 1 $\Rightarrow$ 001, or 010 with the order above.
- The order of JP7 is, then, **10H2**, where H denotes the "half bit" that enables fractional multipliers.

Denoting binary 1 as **O**(pen) and 0 as **C**(losed), I can construct a more complete multiplier table as follows

| Multiplier<br>(210) | Permutation<br>(102) | JP7<br>(10H2) |
| :---: | :---: | :---: |
|2 (2-2=0$\Rightarrow$000)|000|CCCC|
|2.5 | |CCOC|
|3 (3-2=1$\Rightarrow$001)|010|COCC|
|3.5 | |COOC|
|4 (4-2=2$\Rightarrow$010)|100|OCCC|
|4.5 | |OCOC|
|5 (5-2=3$\Rightarrow$011)|110|OOCC|
|5.5 | |OOOC|
|6 (6-2=4$\Rightarrow$100)|001|CCCO|
|6.5 | |CCOO|
|7 (7-2=5$\Rightarrow$101)|011|COCO|
|7.5 | |COOO|
|8 (8-2=6$\Rightarrow$110)|101|OCCO|
|8.5 | |OCOO|
|9 (9-2=7$\Rightarrow$111)|111|OOCO|
|9.5 | |OOOO|

Interesting, but useless. If I had only taken a look at the silkscreen I would've seen a table of the multipliers already available...
{:refdef: style="text-align: center;"}
![](/assets/img/2026-02-24-440bx_3.jpg){:width="70%"}
{: refdef}
...and notice: the silkscreen has 2 as OOOO, the math above said its CCCC, and 9.5 should be OOOO. What's going on here?

Simple: there is no 9.5 multiplier in the board. The logic in the motherboard includes multipliers from 2 to 9, including half-multipliers, and it identifies 2$\leftrightarrow$9.5, i.e., CCCC$\leftrightarrow$OOOO. Not that it matters anyways, because Pentium*!!!* CPUs are multiplier-locked, meaning they get their multiplier from the CPU instead of the motherboard. So all of the above is *super* useless...

...except that there are some Pentium II CPUs which are multiplier unlocked. I don't have any, but I know they're out there. I do have something which I think is better than an unlocked Pentium II: a **Celeron 333 Engineering Sample** with unlocked multipliers. 
{:refdef: style="text-align: center;"}
![](/assets/img/2026-02-24-440bx_4.jpg){:width="70%"}
{: refdef}

With this CPU I confirmed the above: CCCC$\leftrightarrow$OOOO=2. That is, I have a 133 MHz Celeron--at this frequency it turns off the L2 cache! When booting up at 166 MHz (2.5*66), the L2 cache is again enabled.

..and thus, finally building a PC with my Celeron 300A failed *again*, because my focus shifted to building a down-clockable Slot 1 Machine with my Celeron 333 ES.

Welp.

[^1]: ISA suggested it wasn't i810/i815, Socket 370 suggested it wasn't i440LX/i440EX, 3 RAM slots suggested it wasn't i440ZX.
[^2]: Mirrored here too: [User Manual](/assets/files/c94800bv-603bc5a777cbc293693680.pdf), [Spec Sheet](/assets/files/5767at-63e7b14a3ba1a636765320.pdf)