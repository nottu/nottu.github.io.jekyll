---
layout: post
title: Exploiting Cyclic Symmetry in Convolutional Neural Networks
excerpt_separator: <!--more-->
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

The authors of this paper propose four new neural networks, that can be used together to build **CNNs** (Convolutional Neural Networks) that are partially or fully rotation equivariant.

<!--more-->

### Equivariance and Invariance

  A function $f(x)$ is called equivariant to a class of transformations T, if

  $$ f(tx) = t^\prime f(x) \,\,\,\, \forall t \in T$$

  where $t^\prime$ is some transformation of the output. That is, transforming an input $x$ and then passing it to $f$ gives the same result as passing $x$ to $f$ and then transforming the output. Furthermore, a function $f$ is invariant to this class of transformations if

  $$ f(tx) = f(x) \,\,\,\, \forall t \in T$$

### Why encode invariance?

The simplest and most common way to achieve an approximate invariance to a class of transformations of the input is through *data augmentation* during training. But there is no guarantee that this will generalize, to obtain such a thing encoding the desired invariance properties into the network might be helpful.

### Proposed Layers
![Cyclic Operators](/images/cyclic_ops.png)

#### Cyclic Slicing

This layer stacks rotated copies of the input into a single mini-batch, resulting in a $4 \times$ bigger batch.

#### Cyclic Pooling

Combines the predictions from differently rotated copies using a permutation invariant pooling function, reducing the batch size $4 \times$.

#### Cyclic Rolling

Cyclically permutes the input and stacks them along the feature dimension. This increases the number of feature maps which in turn allows us to reduce the number of filters in the convolutional layers. This is similar to $4-$way parameter sharing.

#### Cyclic Stacking

Full rotational equivariance isn't always required and for that use case s simple stack or concatenation of feature maps instead of pooling will suffice.

### Rotating Feature Maps or Filters?

<img src="/images/feature_maps.png" alt="Feature vs Filter" width="400"/>

Rotating feature maps is easier to implement because the roll operator can be isolated in a separate layer. On the other hand, this implies the roll operation has to make four copies of the feature map, increasing memory requirements. Rotating filters requires re-implementing convolutional layers, making implementation more complex, but since only filters are copied memory requirements are lower. The authors of the paper use the former option.

### Final Thoughts

The authors of the paper propose four new layers to be used in CNNs. *Slicing* and *Pooling* can easily be used in existing network architectures to add a degree of equivariance. The results showed in the paper show that networks with these layers perform better than networks with out them and through the use of *Rolling* they managed to reduced the number of training parameters by half or even by four. <!-- I believe further research is required to confirm that  -->