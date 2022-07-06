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
We propose a framework for aligning and fusing multiple images into a single view using neural image representations (NIRs), also known as implicit or coordinate-based neural representations. Our framework targets burst images that exhibit camera ego motion and potential changes in the scene. We describe different strategies for alignment depending on the nature of the scene motion---namely, perspective planar (i.e., homography), optical flow with minimal scene change, and optical flow with notable occlusion and disocclusion. With the neural image representation, our framework effectively combines multiple inputs into a single canonical view without the need for selecting one of the images as a reference frame. We demonstrate how to use this multi-frame fusion framework for various layer separation tasks.


Overview - Neural Image Representations (NIRs) for Multi-Image Fusion
------------------------  
<div style="text-align: center"><img src="{{ site.url }}/research/img/nir/overview_fusion.png" width="80%" alt="overview of multi-image fusion" /></div>
**Figure 1.** Illustration of our neural image representations (NIRs). Assuming that the MLP <i>f</i> learns a canonical view where all burst images are fused, we render each image by projecting the canonical view to the frame-specific view, which is achieved by transforming the input coordinates fed into the <i>f</i>. We estimate the transform using another MLP <i>g</i>. According to different assumptions of the world, we formulate our framework differently; we formulate the transform of coordinates using (a) homography, (b) optical flow without occlusion/disocclusion, and (c) optical flow with occlusion/disocclusion.


Visualization of Canonical View
------------------------  
<div style="text-align: center">
<video width="25%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/vis/vis.mp4" type="video/mp4">
</video>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<img width="50%" src="{{ site.url }}/research/img/nir/results/vis/canview.png" />
</div>
**Figure 2.** Visualization of learned canonical view. We capture 9 consecutive images (left), and fit a homography-based neural representation to them. As can be seen, our method automatically stitches all the images in the canonical view (right) learned in the neural representation.


Overview - Multi-Image Layer Separation
------------------------  
<div style="text-align: center"><img src="{{ site.url }}/research/img/nir/overview_lseparation.png" width="40%" alt="overview of multi-image layer separation" /></div>
**Figure 3.** Overview of our two-stream NIRs for multi-image layer separation. The goal of our method is to separate the underlying scene and interference moving differently in images into two layers stored in a different NIR. To this end, we simultaneously train two NIRs. <i>f</i><sup>1</sup> is parameterized by our homography or flow-based NIRs so as to learn the underlying scene moving according to the explicit motion model. In contrast, the interference layer that is difficult to be modelled by the motion model is stored in <i>f</i><sup>2</sup>. The generic form of image formation is a linear combination of both networks, but varies according to tasks. We also use a few regularizations for optimization, which are described in detail in the paper.



Application 1: Reflection Removal
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
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/reflection/1/input.mp4" type="video/mp4">
</video>
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/li2013.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/gandelsman2019.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/liu2020.png" />
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/reflection/1/ours.mp4" type="video/mp4">
</video>
<br />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/li2013_r.png" style="visibility: hidden;" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/li2013_r.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/gandelsman2019_r.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/1/liu2020_r.png" />
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/reflection/1/ours_r.mp4" type="video/mp4">
</video>
<br />
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/reflection/2/input.mp4" type="video/mp4">
</video>
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/li2013.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/gandelsman2019.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/liu2020.png" />
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/reflection/2/ours.mp4" type="video/mp4">
</video>
<br />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/li2013_r.png" style="visibility: hidden;" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/li2013_r.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/gandelsman2019_r.png" />
<img width="17%" src="{{ site.url }}/research/img/nir/results/reflection/2/liu2020_r.png" />
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/reflection/2/ours_r.mp4" type="video/mp4">
</video>
</div>
**Figure 4.** Comparison of refleciton removal methods on real images. We used the baseline results reproduced by [this](https://alex04072000.github.io/ObstructionRemoval/), where video results are not available.



Application 2: Fence Removal
------------------------  
<div style="text-align: center">
<table style="width:85%; margin-left: auto; margin-right: auto;">
<tr>
  <th style="width:33%; text-align:center;">Input</th>
  <th style="width:33%; text-align:center;">Liu <i>et al.</i>, 2020</th>
  <th style="width:33%; text-align:center;">Ours</th>
</tr>
</table>
<video width="28%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/fence/1/input.mp4" type="video/mp4">
</video>
<img width="28%" src="{{ site.url }}/research/img/nir/results/fence/1/liu2020.png" />
<video width="28%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/fence/1/ours.mp4" type="video/mp4">
</video>
<br />
<img width="28%" src="{{ site.url }}/research/img/nir/results/fence/1/liu2020_f.png" style="visibility: hidden;" />
<img width="28%" src="{{ site.url }}/research/img/nir/results/fence/1/liu2020_f.png" />
<video width="28%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/fence/1/ours_f.mp4" type="video/mp4">
</video>
</div>
**Figure 5.** Comparison of fence removal methods on real images. We used the baseline results reproduced by [this](https://alex04072000.github.io/ObstructionRemoval/), where video results are not available. Note that the gray pixels in the fence layer of Liu et al. indicate empty, which is same as the black pixels in our result.



Application 3: Rain Removal
------------------------  
<div style="text-align: center">
<table style="width:85%; margin-left: auto; margin-right: auto;">
<tr>
  <th style="width:33%; text-align:center;">Input</th>
  <th style="width:33%; text-align:center;">FastDeRain</th>
  <th style="width:33%; text-align:center;">Ours</th>
</tr>
</table>
<video width="28%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/rain/1/input.mp4" type="video/mp4">
</video>
<video width="28%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/rain/1/fastderain.mp4" type="video/mp4">
</video>
<video width="28%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/rain/1/ours.mp4" type="video/mp4">
</video>
<br />
<video width="28%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/rain/2/input.mp4" type="video/mp4">
</video>
<video width="28%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/rain/2/fastderain.mp4" type="video/mp4">
</video>
<video width="28%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/rain/2/ours.mp4" type="video/mp4">
</video>
</div>
**Figure 6.** Comparison of rain removal methods on real images. All results are visualized in videos.



Application 4: Moiré Removal
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
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/moire/1/input.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/moire/1/afn.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/moire/1/c3net.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/moire/1/doubledip.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/moire/1/ours.mp4" type="video/mp4">
</video>
<br />
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/moire/2/input.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/moire/2/afn.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/moire/2/c3net.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/moire/2/doubledip.mp4" type="video/mp4">
</video>
<video width="17%" autoplay loop muted>
  <source src="{{ site.url }}/research/img/nir/results/moire/2/ours.mp4" type="video/mp4">
</video>
</div>
**Figure 7.** Comparison of moiré removal methods on real images. All results are in videos.



Publications
------------

* **Neural Image Representations for Multi-Image Fusion and Layer Separation**<br />
Seonghyeon Nam, Marcus A. Brubaker, Michael S. Brown<br />
*Proc. European Conference on Computer Vision (ECCV) 2022*<br />
[\[arXiv\]](https://arxiv.org/abs/2108.01199)
