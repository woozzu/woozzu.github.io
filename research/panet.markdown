---
layout: research
title:  Cross-Identity Motion Transfer for Arbitrary Objects through Pose-Attentive Video Reassembling
---

Cross-Identity Motion Transfer for Arbitrary Objects<br />through Pose-Attentive Video Reassembling
================================
<div style="text-align: center"><img src="{{ site.url }}/research/img/panet/teasor.png" width="85%" alt="teasor" />
</div>
**Figure 1.** (a) Previous motion transfer methods is based on spatial warping of single image. (b) We propose a non-local search based approach that handles a wide range of motion. (c) A single source image contains insufficient appearance data. (d) Our method can utilize multiple sources with various views. (e) Self-supervision causes identity-leakage in motion transfer. (f) We propose a cross-identity training which is effective in preserving identities of a source image.


Abstract
-------------------------
We propose an attention-based networks for transferring motions between arbitrary objects. Given a source image(s) and a driving video, our networks animate the subject in the source images according to the motion in the driving video. In our attention mechanism, dense similarities between the learned keypoints in the source and the driving images are computed in order to retrieve the appearance information from the source images. Taking a different approach from the well-studied warping based models, our attention-based model has several advantages. By reassembling non-locally searched pieces from the source contents, our approach can produce more realistic outputs. Furthermore, our system can make use of multiple observations of the source appearance (e.g. front and sides of faces) to make the results more accurate. To reduce the training-testing discrepancy of the self-supervised learning, a novel cross-identity training scheme is additionally introduced. With the training scheme, our networks is trained to transfer motions between different subjects, as in the real testing scenario. Experimental results validate that our method produces visually pleasing results in various object domains, showing better performances compared to previous works.


Demo Video
------------------------  
<div style="width: 85%; margin: auto">{% youtube "https://youtu.be/nCELMllynAo" %}</div>
<br />

Overview
------------------------  
<div style="text-align: center"><img src="{{ site.url }}/research/img/panet/overview.png" width="85%" alt="overview" /></div>
**Figure 2.** Overview of our work. It consists of (1) pose-dependent appearance embedding module, (2) pose-attentive retrieval module, and (3) image generation module. The pose-dependent appearance embedding module takes frames in the source video to embed (pose, appearance) pairs. Pose attention block retrieves appearance correspondent to the driving pose. The driving pose is extracted using the shared pose embedding network. Finally, image generation module generates the results.

<div style="text-align: center"><img src="{{ site.url }}/research/img/panet/ciloss.png" width="85%" alt="overview" /></div>
**Figure 3.** Self-reconstruction and cross-identity reconstruction training scheme.


Comparison
------------------------  
<div style="text-align: center"><img src="{{ site.url }}/research/img/panet/results.png" width="75%" alt="overview" /></div>
**Figure 4.** Qualitative results of single source animation. We conduct experiments on VoxCeleb2, Thai-Chi-HD, and BAIR datasets. Source images and driving images represent appearance and pose to condition on, respectively.


Source Code
---------------
Please visit our [github repository](https://github.com/).


Publications
------------

* **Cross-Identity Motion Transfer for Arbitrary Objects through Pose-Attentive Video Reassembling**<br />
Subin Jeon, Seonghyeon Nam, Seoung Wug Oh, Seon Joo Kim<br />
*Proc. European Conference on Computer Vision (ECCV) 2020*<br />
[\[PDF\]](https://arxiv.org/abs/2007.08786)