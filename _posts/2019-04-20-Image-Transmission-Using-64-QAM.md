---
date: 2019-05-16T23:48:05.000Z
layout: post
title: Image Transmission Using 64 QAM via Wired/Wireless Channel
subtitle: 'MATLAB and C++ Implementation'
description: >-
  Transfer image using 64 QAM to reduce network load
image: >-
  https://res.cloudinary.com/dog8hn5qv/image/upload/v1638982168/blog/qam_xulfwh.png
optimized_image: >-
  https://res.cloudinary.com/dog8hn5qv/image/upload/c_scale,w_380/v1638982168/blog/qam_xulfwh.png
category: Project
tags:
  - Matlab
  - Signal Processing
  - Computer Vision
author: harshmittal
paginate: true
---

CLick here for video: [Video Link](https://www.youtube.com/watch?v=-MvTl2pfDNA&ab_channel=HARSHMITTAL)

Basic Code for transmission of the image using 64 QAM. This project was first implemented on Matlab, then on C++. The code was tested on zedboard.


[![Youtube Link](https://res.cloudinary.com/dog8hn5qv/image/upload/v1638982491/blog/qam_play_znvaxg.png)](https://www.youtube.com/watch?v=-MvTl2pfDNA&ab_channel=HARSHMITTAL)



### QAM:

QAM (quadrature amplitude modulation) is a method of combining two amplitude-modulated (AM) signals into a single channel, thereby doubling the effective bandwidth. 
QAM is used with pulse amplitude modulation (PAM) in digital systems, especially in wireless applications.

In a QAM signal, there are two carriers, each having the same frequency but differing in phase by 90 degrees (one-quarter of a cycle, from which the term quadrature arises).
One signal is called the I signal, and the other is called the Q signal. Mathematically, one of the signals can be represented by a sine wave, and the other by a cosine wave. 
The two modulated carriers are combined at the source for transmission. 
At the destination, the carriers are separated, the data is extracted from each, and then the data is combined into the original modulating information.

<img align="center" src="https://www.electronics-notes.com/images/quadrature-amplitude-modulation-64qam-constellation-02.svg" width=500>
