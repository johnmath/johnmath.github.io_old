---
layout: post
title:  "Computing the Cyclic Decomposition and Order of Elements from Symmetric Groups"
date:   2020-09-09 20:35:00 -0400
categories: algorithms
---

## Introduction 

I am currently taking an introductory class in abstract algebra, and we have been learning about different types of groups. One of these groups is called the **Symmetric Group**. The symmetric group defined over any set , $$\Omega$$, is denoted as $$S_{\Omega}$$. This group is comprised of all of the bijections, $$\sigma : \Omega \rightarrow \Omega$$. of the set onto itself, and its group operation is defined as the composition of these bijections. Since we will be looking at finite symmetric groups, we can denote the symmetric group over a finite set of $$n$$ symbols as $S_{n}$.

An example of an element in $$S_{10}$$ could be the permutation (map) $$\sigma$$ that rearranges [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] to be 
[3, 4, 6, 8, 10, 7, 9, 2, 1, 5]. (i.e. $$\sigma([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]) = [3, 4, 6, 8, 10, 7, 9, 2, 1, 5]$$

## Math and Code 


