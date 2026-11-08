---
title: "The fission that never happened"
category: science
thumbnail: posts/fission-mid-render.jpg   # picture on the home page only
tags: [molecular-dynamics, micelles, corrections]
---

For about four months, my notes said that one of my simulated micelles *split in two*.

It was a nice story. A peptide sits inside a ball of detergent molecules. Around a hundred
nanoseconds in, a piece of the micelle breaks off. The micelle's shape, measured by a number
called the **eccentricity**, jumps from nearly round to strongly elongated. Two analyses were put on
hold "until the fission is handled properly".

None of it was true.

## What eccentricity measures

Eccentricity comes from the moments of inertia of a group of atoms: how the mass is spread
along three axes. A sphere gives zero. A cigar or a disc gives something larger.

{% include figure.html src="fission-eccentricity-concept.png" caption="How eccentricity works. (a) Spheres, cigars and discs have different moments of inertia. (b) Eccentricity grows with the axis ratio. (c) A real micelle, measured on its largest aggregate only: nearly round. (d) The same frame with a few stray detergent molecules included: the 'shape' becomes a long ellipse, because the number is now measuring the distance between the pieces." %}

Panel (d) is the whole story. I had computed the eccentricity over *every* detergent molecule in
the box. Most of them formed one micelle; a handful sat elsewhere as a small separate cluster.
The inertia tensor does not know these are separate objects. It reports one big elongated object
spanning both, so the number measured the *gap between* the pieces, not the shape of either one.

## There was never a split

Once the number was suspect, the obvious next question was: when did the small cluster break off?
So I counted aggregates in every frame, starting from the very first structure.

The small cluster was there at time zero. That system had never been a single micelle. It was
built from loosely scattered detergent, equilibration gathered most of it into one aggregate, and
a few molecules simply never joined. In one system the small group kept exactly the same members for
280 nanoseconds. Nothing budded off, because nothing had ever been attached.

{% include figure.html src="fission-mid-render.jpg" caption="The same system drawn on its main aggregate only: the peptide is buried in a normal, roughly round micelle." %}

Measured on the largest aggregate alone, the micelle's eccentricity was ordinary, in the same
range as every other micelle I had simulated. And the peptide was inside the main aggregate in
every frame, so the analyses that had waited for months on the "fission" needed no fixing at all.

## Why it took so long

Not because anyone was careless, which is the uncomfortable part.

- Forty-six of sixty molecules in one ball looks completely convincing as "the micelle".
- The stray molecules sat elsewhere in the box, easy to overlook.
- My own render script drew only molecules joined to the main aggregate, so every picture I
  looked at quietly hid the evidence.
- A notebook entry that says "fission at ~105 ns" gets copied forward. Each copy makes it look
  more established.

The fix was not cleverness. It was going back to the first frame and counting.

What I take from it: **a story is not a measurement.** The moment a number has a story attached
to it, I stop questioning the number. Now, when I write down an explanation, I also write down
the observation that would prove it wrong, and I go and look for it.
