---
layout: post
title:  "Computing the Cyclic Decomposition and Order of Elements from Symmetric Groups"
date:   2020-09-09 20:35:00 -0400
categories: algorithms
---

## Introduction 

I am currently taking an introductory class in abstract algebra, and we have been learning about different types of groups. One of these groups is called the **Symmetric Group**. The symmetric group defined over any set , $$\Omega$$, is denoted as $$S_{\Omega}$$. This group is comprised of all of the bijections, $$\sigma : \Omega \rightarrow \Omega$$. of the set onto itself, and its group operation is defined as the composition of these bijections. Since we will be looking at finite symmetric groups, we can denote the symmetric group over a finite set of $$n$$ symbols as $S_{n}$.

An example of an element in $$S_{10}$$ could be the permutation (map) $$\sigma$$ that rearranges [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] to be 
[3, 4, 6, 8, 10, 7, 9, 2, 1, 5]. 

(i.e. $$\sigma([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]) = [3, 4, 6, 8, 10, 7, 9, 2, 1, 5]$$)

Now that we know how the elements of $$S_{n}$$ act on the underlying set, what are their cyclic decompositions and orders? The **order** of an element in a group refers to the smallest positive integer, $$m$$ such that $$\sigma^{m} = \sigma \circ \sigma \circ ... \circ \sigma = \textbf{id}$$ (\textbf{id} is that group's identity element). The **cyclic decomposition** of one of these group elements refers to the "cycles" formed when repeatedly applying the same permutation on the underlying set. In other words, the cyclic decomposition refers to the "path" that each individual set element takes under a repeated permutation to get mapped back to itself.

Viewing the permutation as a mapping of individual elements instead of a rearrangement of the entire set can aid in understanding how cyclic decompositions and repeated permutations work. Using the $$\sigma$$ that we defined above, we can write out the following mapping:

$$
\newline 1 \mapsto  3
\newline 2 \mapsto 4
\newline 3 \mapsto 6
\newline 4 \mapsto 8
\newline 5 \mapsto 10
\newline 6 \mapsto 7
\newline 7 \mapsto 9
\newline 8 \mapsto 2
\newline 9 \mapsto 1
\newline 10 \mapsto 5
$$ 

## Math and Code 


