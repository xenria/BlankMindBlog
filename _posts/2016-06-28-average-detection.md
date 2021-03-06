---
layout: post
title: Experiment of Average detection
date: 2016-06-28 00:00:00
type: post
published: true
status: publish
categories: []
tags: []
description: average detection of RSSi over time.   

author: tiara
---

Because we no longer have class on Tuesdays, we are at ARUP conducting experiments. Two things we need to find out: which RPi is better at receiving information(Rpi 2 or 3) and what is the average detection of RSSi over Time. 

# Experiment: Average detection and comparison of Rpi 2 vs 3 

### Stationary and moving with Rpi 2 vs Rpi 3 

Testing for: which one is more accurate. 
How: Which one picks up the strongest rpi(more fluctuation or less, more frequent received RSSi or not)

### Method: 

Time: we experiment 1, min 2 minute 10 minutes and found it wasn't a long enough time period to determine the average number of detections over time. Therefore we will try it for 1 hr this time. That is a long time for someone to be standing in one position so we will hang the beacon from the ceiling on a string instead. 

### Set up 

> Rpi --> 1m --> 2m --> 3m --> 4m --> 5m --> 6m --> 7m --> 8m --> 9m --> 10m 
>
> ----------------------|o| Rpi 2
> ----------------------|o| Rpi 3

### Analysis 

> TD/TT = A
>
> TD = Total detection over a period of time. 
> TT = Total time 
> A  = Average detection of RSSi for a distance, 

![set up 1]({{ site.baseurl }}/assets/setup1.jpg)

![set up 2]({{ site.baseurl }}/assets/setup2.jpg)

![set up 3]({{ site.baseurl }}/assets/setup3.jpg)

![set up 4]({{ site.baseurl }}/assets/setup4.jpg)



