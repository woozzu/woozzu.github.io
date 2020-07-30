---
layout: research
title:  A Holistic Approach to Cross-Channel Image Noise Modeling and its Application to Image Denoising
---

A Holistic Approach to Cross-Channel Image Noise Modeling and its Application to Image Denoising
================================

Abstract
-------------------------

Modelling and analyzing noise in images is a fundamental task in many computer vision systems. Traditionally, noise has been modelled per color channel assuming that the color channels are independent. Although the color channels can be considered as mutually independent in camera RAW images, signals from different color channels get mixed during the imaging process inside the camera due to gamut mapping, tone-mapping, and compression. We show the influence of the in-camera imaging pipeline on noise and propose a new noise model in the 3D RGB space to accounts for the color channel mix-ups. A data-driven approach for determining the parameters of the new noise model is introduced as well as its application to image denoising. The experiments show that our noise model represents the noise in regular JPEG images more accurately compared to the previous models and is advantageous in image denoising.


Source Code
---------------
Please visit our [github repository](https://github.com/woozzu/ccnoise).

To run demo,

* Create a dataset from temporal images: run `demo_dataset.m`
* Create training data: run `train/demo_create_training_data.py`
* Train a multi-layer perceptron (MLP): run `caffe train -solver=train/solver.prototxt`
* Estimate the noise parameters of a test image using a trained MLP: run `demo_estimation.m`


Dataset
------------------------  
Our dataset consists of 11 static scenes captured by 3 consumer cameras. For each scene, 500 temporal images were captured to compute temporal mean image and covariance matrix for each pixel. However, this package only contains one of the 500 images for size limit, with precomputed temporal mean and covariance matrix data. For detailed information, please refer to the paper and supplementary material.

The size of our dataset is about 10GB. You can download it via [a dropbox link](https://www.dropbox.com/s/24kds7c436i5i11/real_image_noise_dataset.zip?dl=0).


Publications
------------

* **A Holistic Approach to Cross-Channel Image Noise Modeling and its Application to Image Denoising**<br />
Seonghyeon Nam\*, Youngbae Hwang\*, Yasuyuki Matsushita, Seon Joo Kim<br />
*Proc. IEEE Conference on Computer Vision and Pattern Recognition (CVPR) 2016 **[Spotlight]***<br />
[\[PDF\]]({{ site.url }}/assets/publication/ccnoise_cvpr16/ccnoise_cvpr16.pdf) [\[supplementary material\]]({{ site.url }}/assets/publication/ccnoise_cvpr16/ccnoise_cvpr16_supp.pdf) [\[bibtex\]]({{ site.url }}/assets/publication/ccnoise_cvpr16/ccnoise_cvpr16.txt)