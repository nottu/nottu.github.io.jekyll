---
layout: post
title: Exploiting Cyclic Symmetry in Convolutional Neural Networks
---

[Source](https://arxiv.org/abs/1602.02660)

<table class='authors'>
  <tr>
    <td>Sander Dielman</td>
    <td class="email"><a href="mailto:SEDIELEM@GOOGLE.COM">SEDIELEM@GOOGLE.COM</a></td>
  </tr>
  <tr>
    <td>Jeffrey De Fauw</td>
    <td class="email"><a href="mailto:DEFAUW@GOOGLE.COM">DEFAUW@GOOGLE.COM</a></td>
  </tr>
  <tr>
    <td>Koray Kavukcuoglu</td>
    <td class="email"><a href="mailto:KORAYK@GOOGLE.COM">KORAYK@GOOGLE.COM</a></td>
  </tr>
</table>

<br/>

<!-- In this paper the use of four new operations that are aimed to introduce rotational equivariance in **convolutional neural networks** (*CNNs*) is discussed. -->

The authors of this paper propose four new neural networks, that can be used together to build **CNNs** (Convolutional Neural Networks) that are partially or fully rotation equivariant.

### Equivariance and Invariance

  A function $f(x)$ is called equivariant to a class of transformations T, if

  $$ f(tx) = t^\prime f(x) \,\,\,\, \forall t \in T$$

  where $t^\prime$ is some transformation of the output. That is, transforming an input $x$ and then passing it to $f$ gives the same result as passing $x$ to $f$ and then transforming the output. Furthermore, a function $f$ is invariant to this class of transformations if

  $$ f(tx) = f(x) \,\,\,\, \forall t \in T$$

