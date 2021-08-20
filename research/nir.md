---
layout: research
title:  Neural Image Representations for Multi-Image Fusion and Layer Separation
---

Neural Image Representations<br />for Multi-Image Fusion and Layer Separation
================================
<div style="text-align: center">
<a href="http://snam.ml" target="_blank">Seonghyeon Nam</a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://mbrubake.github.io/" target="_blank">Marcus A. Brubaker</a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a href="http://www.cse.yorku.ca/~mbrown" target="_blank">Michael S. Brown</a><br />
York University
</div>


Abstract
-------------------------
We propose a framework for aligning and fusing multiple images into a single coordinate-based neural representations. Our framework targets burst images that have misalignment due to camera ego motion and small changes in the scene. We describe different strategies for alignment depending on the assumption of the scene motion, namely, perspective planar (i.e., homography), optical flow with minimal scene change, and optical flow with notable occlusion and disocclusion. Our framework effectively combines the multiple inputs into a single neural implicit function without the need for selecting one of the images as a reference frame. We demonstrate how to use this multi-frame fusion framework for various layer separation tasks.


Overview - Multi-Image Fusion
------------------------  
<div style="text-align: center"><img src="{{ site.url }}/research/img/nir/overview_fusion.png" width="60%" alt="overview of multi-image fusion" /></div>
**Figure 1.** Overview of the neural image representations for multi-image fusion. Assuming that <i>f</i>(<i>x</i>, <i>y</i>) learns a canonical view that summarizes all input images, the rendering of each image is formulated as a projection of the canonical view onto the view of the image. According to the assumption of the world, we use different parameterization of motion such as (a) homography-based neural representations, (b) occlusion-free flow-based neural representations, and (c) occlusion-aware flow-based neural representations. Unlike conventional multi-image fusion working on discrete 2D grids, our method fuses multiple images in a continuous image space. In addition, our method does not rely on a reference image manually selected among input images.


Visualization of Canonical View
------------------------  
<div style="text-align: center">
<video width="25%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/vis/vis.mp4" type="video/mp4">
</video>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<img width="50%" src="{{ site.url }}/research/img/nir/results/vis/canview.png" />
</div>
**Figure 2.** Visualization of learned canonical view. We capture 9 consecutive images (left), and fit a homography-based neural representation to them. As can be seen, our method automatically stitches all the images in the canonical view (right) learned in the neural representation.


Overview - Multi-Image Layer Separation
------------------------  
<div style="text-align: center"><img src="{{ site.url }}/research/img/nir/overview_lseparation.png" width="40%" alt="overview of multi-image layer separation" /></div>
**Figure 3.** Overview of our two-stream neural representations for multi-image layer separation. The goal of our method is to separate the underlying scene and interference moving differently in images into two layers stored in a different neural representation. To this end, we simultaneously train two neural image representations. <i>f</i><sup>1</sup> is parameterized by our homography or flow-based neural representations so as to learn the underlying scene moving according to the explicit motion model. In contrast, the interference layer that is difficult to be modelled by the motion model is stored in <i>f</i><sup>2</sup>. The generic form of image formation is a linear combination of both networks, but varies according to tasks. We also use a few regularizations for optimization, which are described in detail in the paper.


Application 1: Moiré Removal
------------------------  
<div style="text-align: center">
<table style="width:86%; margin-left: auto; margin-right: auto;">
<tr>
  <th style="width:20%; text-align:center;">Input</th>
  <th style="width:20%; text-align:center;">AFN</th>
  <th style="width:20%; text-align:center;">C3Net</th>
  <th style="width:20%; text-align:center;">Double DIP</th>
  <th style="width:20%; text-align:center;">Ours</th>
</tr>
</table>
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/moire/1/input.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/moire/1/afn.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/moire/1/c3net.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/moire/1/doubledip.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/moire/1/ours.mp4" type="video/mp4">
</video>
<br />
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/moire/2/input.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/moire/2/afn.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/moire/2/c3net.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/moire/2/doubledip.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/moire/2/ours.mp4" type="video/mp4">
</video>
</div>
**Figure 4.** Comparison of moiré removal methods on real images. All results are in videos.


Application 2: Reflection Removal
------------------------  
<div style="text-align: center">
<table style="width:86%; margin-left: auto; margin-right: auto;">
<tr>
  <th style="width:20%; text-align:center;">Input</th>
  <th style="width:20%; text-align:center;">Li <i>et al.</i>, 2013</th>
  <th style="width:20%; text-align:center;">Double DIP</th>
  <th style="width:20%; text-align:center;">Liu <i>et al.</i>, 2020</th>
  <th style="width:20%; text-align:center;">Ours</th>
</tr>
</table>
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/reflection/1/input.mp4" type="video/mp4">
</video>
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/li2013.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/gandelsman2019.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/liu2020.png" />
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/reflection/1/ours.mp4" type="video/mp4">
</video>
<br />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/li2013_r.png" style="visibility: hidden;" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/li2013_r.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/gandelsman2019_r.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/liu2020_r.png" />
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/reflection/1/ours_r.mp4" type="video/mp4">
</video>
<br />
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/reflection/2/input.mp4" type="video/mp4">
</video>
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/li2013.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/gandelsman2019.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/liu2020.png" />
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/reflection/2/ours.mp4" type="video/mp4">
</video>
<br />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/li2013_r.png" style="visibility: hidden;" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/li2013_r.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/gandelsman2019_r.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/liu2020_r.png" />
<video width="17%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/reflection/2/ours_r.mp4" type="video/mp4">
</video>
</div>
**Figure 5.** Comparison of refleciton removal methods on real images. We collected the baseline results from [here](https://alex04072000.github.io/ObstructionRemoval/). Thus, we do not have video results.


Application 3: Fence Removal
------------------------  
<div style="text-align: center">
<table style="width:85%; margin-left: auto; margin-right: auto;">
<tr>
  <th style="width:33%; text-align:center;">Input</th>
  <th style="width:33%; text-align:center;">Liu <i>et al.</i>, 2020</th>
  <th style="width:33%; text-align:center;">Ours</th>
</tr>
</table>
<video width="28%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/fence/1/input.mp4" type="video/mp4">
</video>
<img width="28%" src="{{ site.url }}/research/img/nir/results/fence/1/liu2020.png" />
<video width="28%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/fence/1/ours.mp4" type="video/mp4">
</video>
<br />
<img width="28%" src="{{ site.url }}/research/img/nir/results/fence/1/liu2020_f.png" style="visibility: hidden;" />
<img width="28%" src="{{ site.url }}/research/img/nir/results/fence/1/liu2020_f.png" />
<video width="28%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/fence/1/ours_f.mp4" type="video/mp4">
</video>
</div>
**Figure 6.** Comparison of fence removal methods on real images. We collected the baseline results from [here](https://alex04072000.github.io/ObstructionRemoval/). Thus, we do not have video results. Note that the gray pixels in the fence layer of Liu et al. indicate empty, which is same as the black pixels in our result.


Application 4: Rain Removal
------------------------  
<div style="text-align: center">
<table style="width:85%; margin-left: auto; margin-right: auto;">
<tr>
  <th style="width:33%; text-align:center;">Input</th>
  <th style="width:33%; text-align:center;">FastDeRain</th>
  <th style="width:33%; text-align:center;">Ours</th>
</tr>
</table>
<video width="28%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/rain/1/input.mp4" type="video/mp4">
</video>
<video width="28%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/rain/1/fastderain.mp4" type="video/mp4">
</video>
<video width="28%" autoplay loop>
  <source src="{{ site.url }}/research/img/nir/results/rain/1/ours.mp4" type="video/mp4">
</video>
</div>
**Figure 7.** Comparison of rain removal methods on real images. All results are in videos.



Publications
------------

* **Neural Image Representations for Multi-Image Fusion and Layer Separation**<br />
Seonghyeon Nam, Marcus A. Brubaker, Michael S. Brown<br />
*arXiv preprint arXiv:2108.01199, 2021*<br />
[\[arXiv\]](https://arxiv.org/abs/2108.01199)