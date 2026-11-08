---
title: "Meet AsCATH5, the peptide I spend my days with"
category: research
thumbnail: posts/meet-ascath5-1000ns.jpg   # picture on the home page only
tags: [ascath5, nmr, molecular-dynamics]
---

Most of my PhD is about one molecule. It is twenty-two amino acids long, it comes from the
Chinese alligator, and it kills bacteria. Its name is **AsCATH5**.

```
T R R K F W K K V L N G A L K I A P F L L G
```

AsCATH5 is a *cathelicidin*, one of the antimicrobial peptides that animals make as a first line of
defence. Count the letters R and K in that sequence: arginines and lysines, both positively charged.
Four of the six sit in the first eight positions. That cluster of positive charge is the first clue
to how the peptide works.

## The question

A bacterial membrane and one of our own cell membranes are both thin sheets of lipid. But
bacterial membranes carry many *negatively* charged lipids, while the outer surface of our cells is
mostly neutral. A peptide covered in positive charge should be pulled towards the bacteria and
leave us alone, and roughly speaking, that is what happens.

"Roughly speaking" is where my project lives. *Which* part of the peptide does the recognising?
Does it matter how the peptide is folded, how deep it sits, which way it faces? And when two
peptides land on the same membrane, do they help each other or get in each other's way?

## Looking at it two ways

The first way is **NMR spectroscopy**. Free in water, AsCATH5 is floppy, with no fixed shape.
In detergent micelles, small balls of soap-like molecules that stand in for a membrane, it
folds into a helix. NMR lets me measure that structure residue by residue.

{% include figure.html src="meet-ascath5-nmr-ensembles.png" caption="AsCATH5 structures calculated from NMR data in two kinds of detergent micelle. Each picture overlays twenty models: where they agree, the helix is well defined; where they splay apart, at the ends, the peptide is flexible. Positively charged side chains in blue, proline 18 in magenta." %}

The second way is **molecular dynamics**: a computer simulation that moves every atom a tiny
step at a time, according to the forces between them, billions of times over.

{% include figure.html src="meet-ascath5-md-explainer.png" caption="Molecular dynamics in four panels: atoms as balls on springs, forces between them, one tiny time step repeated, and the result, a movie." %}

The movie is the fun part. I start the peptide just above a model bacterial membrane and watch.

<div class="figure-pair">
{% include figure.html src="meet-ascath5-0ns.jpg" caption="0 ns: the peptide starts above the membrane." %}
{% include figure.html src="meet-ascath5-1000ns.jpg" caption="1000 ns later: it has settled onto the surface." %}
</div>

A microsecond of simulated time sounds like nothing. It is five hundred million time steps and
days of GPU time. One thing I have learned this year is how much patience that takes, and how
easy it is to mistake "not finished yet" for "finished".

## Why two methods?

Because each one lies in its own way. NMR tells me what the real peptide does, but averaged over
everything and only in micelles. Simulations show me every atom, but only as well as the force
field that drives them, and only for as long as I can afford to run them. When the two agree I
believe them a little more, and when they disagree I learn where to look.

I'll write more about both, including the mistakes. There have been plenty.
