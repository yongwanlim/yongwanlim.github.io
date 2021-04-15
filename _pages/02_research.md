---
layout: page
permalink: /research/
title: research
description: Current research projects

---
### **Real-time Magnetic Resonance Imaging**
My research has mainly focused on the development of novel MRI acquisition, reconstruction, and post-processing methods based on signal processing, mathematical optimization, and machine and deep learning. A majority of my research effort has been dedicated to overcoming fundamental imaging trade-offs and enabling rapid imaging with high quality, large spatial coverage, and low latency. 


<p align="center"> 
<img src="/assets/img/rt_mri_tradeoff.png">
</p>

-------

#### **3D real-time imaging**
_Can real-time MRI technique help us understand speech production better?_  

Real-time MRI technique can visualize moving vocal organs that are involved in speech production such as the tongue, lips, and velum, at relatively high temporal and spatial resolution. However, current methods can only visualize one or a few 2D imaging planes at a time, which provides an incomplete view of the relevant anatomy. This is mainly due to MRI tradeoffs among several imaging parameters: increasing one requires to sacrifice another, for example, temporal resolution versus spatial coverage. 

In this project, we develop and demonstrate "first-ever" volumetric real-time MRI of speech production that enables visualization of the entire vocal organs at high temporal and spatial resolution during natural speech production. 

The below image demonstrates 3D tongue and vocal tract shape features that were never previously visualized.   

<p align="center"> 
<img src="/assets/img/3drtmri_gif.gif">
</p>

Related publications
* Z Zhao, **Y Lim**, D Byrd, S Narayanan, and KS Nayak, Improved 3D real-time MRI of speech production, _Magnetic Resonance in Medicine_, vol. 85, no. 6, pp. 3182-3195, 2021. 
* **Y Lim**, Y Zhu, SG Lingala, D Byrd, S Narayanan, and KS Nayak, 3D dynamic MRI of the vocal tract during natural speech, _Magnetic Resonance in Medicine_, vol. 81, no. 3, pp. 1511–1520, 2019.

-------

#### **Image deblurring**
_Can we achieve better image quality for real-time MRI?_

While spiral-sampling-based MRI technique enables time-efficient imaging, its vulnerability to image artifacts remains challenging and often existing techniques to addressing artifacts rely on computationally expensive methods, making them infeasible to adopt in some applications.

One example of image artifacts in speech production imaging is **blurring** that appears most severely at vocal organs' boundaries and that also varies over time as organs move. This artifact stems from what is called _off-resonance effect_ and the mitigation of this artifact is critical to improving depiction and tracking of vocal articulators for real-time MRI. 

In this project, we focus on the development of fast, small, and computationally effective deep learning techniques that can achieve low-latency deblurring, by designing a model-based
training data generation framework, a minimal convolutional neural network, and an attention-gated
mechanism. We demonstrated low-latency (<20msec per frame) deblurring is possible with comparable quality to conventional approaches (>1sec). We validated artifact mitigation techniques in a large in vivo data corpus and demonstrated increased image sharpness as well as improved usability and interpretability of the acquired data and result in data analysis.

<p align="center"> 
<img src="/assets/img/dorc_gif.gif">
</p>

Related publications
* **Y Lim**, S Narayanan, and KS Nayak, Attention-gated convolutional neural networks for off-resonance correction of spiral real-time MRI, _in Proc. 28th ISMRM Scientific Sessions_, Virtual Conference, April 2020.
* **Y Lim**, Y Bliesener, S Narayanan, and KS Nayak, Deblurring for spiral real-time MRI using convolutional neural networks, _Magnetic Resonance in Medicine_, vol. 84, no. 6, pp. 3438–3452, Dec. 2020.
* **Y Lim**, SG Lingala, S Narayanan, and KS Nayak, Dynamic off-resonance correction for spiral real-time MRI of speech, _Magnetic Resonance in Medicine_, vol. 81, no. 1, pp. 234–246, Jan. 2019.

-------

#### **A public speech production MRI dataset**
Real-time MRI of human speech production is enabling significant advances in speech science, linguistics, bioinspired speech technology development, and clinical applications. However, easy access to this technique is limited, and comprehensive datasets with broad access are needed. 

In an interdisciplinary team effort, I have contributed to the development of a unique data corpus of multimodal speech production MRI data from an unprecedented number of 75 subjects. 

This dataset will offer the linguistics and speech sciences, computational imaging, and engineering community an opportunity to help understand human speech production better and develop advanced computational algorithms for imaging. 

<p align="center"> 
<img src="/assets/img/75subj.png">
</p>

Related publications
* **Y Lim**, A Toutios, et al, A multispeaker dataset of raw and reconstructed speech production real-time MRI video and 3D volumetric images, arXiv:2102.07896, 2021.

-------
