---
layout: post
title: Group Equivariant Convolutional Networks
use_math: true
tags: [CNN, 'rotation-equivariant', 'rotation-invariant'] 
excerpt_separator: <!--more-->
---

[Source](https://arxiv.org/abs/1602.07576)

<table class='authors'>
  <tr>
    <td>Taco S Cohen</td>
    <td class="email"><a href="mailto:SEDIELEM@GOOGLE.COM">T.S.COHEN@UVA.NL</a></td>
  </tr>
  <tr>
    <td>Max Welling</td>
    <td class="email"><a href="mailto:DEFAUW@GOOGLE.COM">M.WELLING@UVA.NL</a></td>
  </tr>
</table>

The paper introduces Group-Convolutions, a type of layer that has a greater degree of weight sharing than regular convolutions by exploiting *symmetries*. Convolutional layers are translation equivariant, that is, shifting an image before passing it through a layer is the same as passing the image and then shifting the result (discarding edge-effects). In other words, *translation symmetry* is preserved
by convolutional layers. In the paper, the authors show how convolutional networks can be generalized to exploit larger groups of *symmetries* (*rotations* and *reflections*).

<!--more-->

