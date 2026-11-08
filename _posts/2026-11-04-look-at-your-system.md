---
title: "Look at your system"
category: science
thumbnail: posts/look-micelle-final.jpg   # picture on the home page only
tags: [molecular-dynamics, visualisation, lessons]
---

Every simulation I run passes a set of checks before I trust it. Count the atoms. Check the box
size. Make sure every lipid is in the right leaflet. Check that nothing is overlapping. These checks
are automatic, fast and reassuring.

This autumn I decided that every system I build should also be **drawn**: a picture, rendered
from the real coordinates, in my weekly report. It felt like a formality. It wasn't.

## What the pictures found

In one week of rendering old systems, I found four problems that every numerical check had passed.

**A pair of peptides in the wrong place.** For one series of simulations I build two peptides
in the water above a membrane and let them settle onto it before the real experiment starts. In
three of the four membranes they started a short way above the surface. In the fourth, the
picture showed them much farther up, near the top of the box.

{% include figure.html src="look-popc-pair-as-built.jpg" caption="The starting structure as built: two peptides (top) far above the membrane surface, before the settling stage. The atom count, box and leaflet checks were all fine." %}

It turned out not to matter. The peptides sank onto the membrane during the settling stage and
ended up just like the others. But I only know that because I went back and checked, and I would
never have checked without the picture.

**Peptides that looked broken.** Some renders showed helices with chunks missing. My first guess
was the rule that hides atoms lying outside the periodic box. The real cause was duller: the
script only drew atoms inside a fixed slab of depth, and some peptides were longer than the slab.
The simulation was fine; the picture was lying.

**A buried peptide that looked exposed.** For micelles, the script rotated the view so the peptide
faced the camera and hid the detergent in front of it. That works when the peptide sits on the
surface. When the peptide is *inside* the micelle, it makes a buried peptide look like it is
sitting on the outside.

**An invisible box.** The outline of the simulation box never appeared, because the ray tracer
ignores line widths. Small, but a picture of a periodic system without its box hides exactly the
thing you need to judge it.

<div class="figure-pair">
{% include figure.html src="look-micelle-start.jpg" caption="A peptide placed on the surface of a micelle at the start of a simulation." %}
{% include figure.html src="look-micelle-final.jpg" caption="The same system at the end: the peptide has moved into the micelle." %}
</div>

## The lesson

Numbers answer the questions you thought to ask. A picture answers questions you didn't think of,
like "why are those peptides up there?".

But pictures also need checking. Half of the problems above were in the *picture*, not the
simulation. A render is a measurement like any other, made by a script with its own assumptions.

So now I do both. Every system gets its numbers checked and its picture drawn, and when the two
disagree, I find out which one is wrong.
