---
title: "Persistent Homology Tutorial for the R-TDA Package"
author: "Robin Belton"
date: "July 29, 2019"
output: html_document
---

{% include lib/mathjax.html %}





Introduction
============
In the Rips tutorial, we looked at the Rips complex which is a method of how one can build a
"shape" out of point cloud data. The Rips complex depends on a parameter, $r$, which we can vary
in order to obtain a Rips filtration. Once we have this filtration, we can study how the homology
classes change at each state of the filtration. We will see later how this can provide meaningful
interpretations of our data. More generally, for *any* type of filtration (does not need to be a
Rips filtration) we can study how the homology classes change. This is *persistent homology*. 

Objectives
==========
**TODO: Make objectives stronger.**
* Be able to define Persistent Homology.
* Learn a few exciting applications of Persistent Homology.
* Compute a Persistent Dagram from a Rips filtration using the R-TDA package.

Theory
======

First we breifly describe the mathematical foundations behind Persistent Homology (PH) including
PH groups and Persistence Diagrams (PD). For consistency, we use the same notation as section
seven of {% cite edelsbrunner:2010 %} and refer the reader to this text for more details on PH
and homology in general.

### PH groups

Let $$K$$ be a simplicial complex and let 

$$\emptyset \subset K_0 \subset K_1 \subset ... \subset K_n=K$$

be a filtration on $$K$$. Let $$\text{include}_{j,m}:K_i\rightarrow K_j$$ be the inclusion map
from $$K_i$$ to $$K_j$$ for $$i\leq j$$. These inclusion maps induce homomorphisms,
$$f^{i,j}_{p}:H_p(K_i, R)\rightarrow H_p(K_j)$$, between the $$p^{th}$$ homology groups of
$$K_i$$ and $$K_j$$ for every dimension $$p$$. 
Therefore, our filtration induces a sequence of homology groups:

$$\emptyset \rightarrow H_p(K_0)\rightarrow H_p(K_1) \rightarrow ... \rightarrow H_p(K_n).$$
As we travel through the sequence, new homology classes form while other homology classes merge
with one another. In PH, the *Elder Rule* holds which states that when two homology classes merge
to form a new homology class, the older class continues while the younger class ends.

The images of the homomorphisms, $$H_p^{i,j}:= $$im$$f^{i,j}_p$$, are the *$$p^{th}$$ persistent
homology groups*. The ranks of the corresponding persistent homology groups are the *$$p^{th}$$
persistent Betti numbers.* 

Let us work through an example to help us synthesize these definitions. Referring back to the
Rips filtration tutorial, consider the Rips filtration we computed for
$$S:=\{(0,0),(1,3),(2,-1),(3,2)\}$$.

<center>
<embed width="90%" src="../../assets/tda-rips/ripsfilt.svg" type="image/svg+xml" />
</center>

So the Rips filtration corresponding to $$S$$ is the following sequence of subcomplexes:

$$\emptyset \subset \text{VR}(S,0) \subset \text{VR}(S, \sqrt{5}) \subset \text{VR}(S, \sqrt{10})
\subset \text{VR}(S, \sqrt{13}) \subset \text{VR}(S, \sqrt{17}).$$

If we compute the integral 0-homology groups for each of these subcomplexes, then we get the
following induced sequence of homology groups:

$$\emptyset \rightarrow \mathbb{Z}^{4} \rightarrow \mathbb{Z}^{2} \rightarrow \mathbb{Z} \rightarrow \mathbb{Z} \rightarrow \mathbb{Z}.$$

Therefore, $$H_0^{0,1}(S,\mathbb{Z})=\mathbb{Z}^2$$ and $$H_0^{2,3}(S,\mathbb{Z})=\mathbb{Z}$$
and so forth. 

We go through a similar procedure to compute the PH groups for higher dimensions. 

**Note:** We can compute PH groups for any type of filtration, it does not need to be a Rips
filtration. There many different types of filtrations including height filtrations, Cech
filtrations, and lower star filtrations to name a few. 

## Persistence Diagrams

At this point you may be thinking that PH groups are cool, but how can we organize all this
information!? This is where PDs come into play. PDs are a topological descriptor of data that
keeps track of all the PH groups that arise from a filtrartion. More specifically, a *$$p^{th}$$
dimensional* PD is multiset of points in the extended plane along with the diagonal where each
point on the diagonal has countably infinite multiplicity. Each PD corresponds to a filtration.
If $$(x,y)$$ is a point in the PD, then $$x$$ denotes the filtration value for which a new
$$p^{th}$$ dimensional homology class emerged or was *born* while $$y$$ denotes the filtration
value for when that homology class ends or *dies*. Note that some homology classes never die
which is denoted by taking $$y=\infty$$. The vertical distance of the point $$(x,y)$$ to the
diagonal is the *persistence* of the homology class corresponding to $$(x,y)$$. 

Let's compute the zeroth dimensional PD for Rips filtration of $$S$$.


