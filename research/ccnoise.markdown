---
layout: research
title:  A Holistic Approach to Cross-Channel Image Noise Modeling and its Application to Image Denoising
---

A Holistic Approach to Cross-Channel Image Noise Modeling and its Application to Image Denoising
================================

Abstract
-------------------------

Modelling and analyzing noise in images is a fundamental task in many computer vision systems. Traditionally, noise has been modelled per color channel assuming that the color channels are independent. Although the color channels can be considered as mutually independent in camera RAW images, signals from different color channels get mixed during the imaging process inside the camera due to gamut mapping, tone-mapping, and compression. We show the influence of the in-camera imaging pipeline on noise and propose a new noise model in the 3D RGB space to accounts for the color channel mix-ups. A data-driven approach for determining the parameters of the new noise model is introduced as well as its application to image denoising. The experiments show that our noise model represents the noise in regular JPEG images more accurately compared to the previous models and is advantageous in image denoising.


Datasets.
------------------------  
Our dataset consists of 11 static scenes captured by 3 consumer cameras. For each scene, 500 temporal images were captured to compute temporal mean image and covariance matrix for each pixel. However, this package only contains one of the 500 images for size limit, with precomputed temporal mean and covariance matrix data. For detailed information, please refer to the paper and supplementary material.

We did not upload our dataset yet for size limit (our dataset is 10GB). So, please contact us via [email](mailto:shnnam@yonsei.ac.kr) if you need.


Publications
------------

* **A Holistic Approach to Cross-Channel Image Noise Modeling and its Application to Image Denoising**<br />
Seonghyeon Nam\*, Youngbae Hwang\*, Yasuyuki Matsushita, Seon Joo Kim<br />
*Proc. IEEE Conference on Computer Vision and Pattern Recognition (CVPR) 2016 **[Spotlight]***<br />
[\[PDF\]]({{ site.url }}/assets/ccnoise_cvpr16/ccnoise_cvpr16.pdf) [\[supplementary material\]]({{ site.url }}/assets/ccnoise_cvpr16/ccnoise_cvpr16_supp.pdf) [\[bibtex\]]({{ site.url }}/assets/ccnoise_cvpr16/ccnoise_cvpr16.txt)