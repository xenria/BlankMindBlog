---
layout: post
title: BVN floor plan and Shortest path algorithm 
date: 2016-06-23 09:00:00
type: post
published: true
status: publish
categories: []
tags: []
description: Bring on the pain, BVN floorspace shortest path algorithm within grasshopper finished

author: tiara
---

Part of accomplishing task 1, Anniza and I split the work for getting both the BVN and the ARUP floor plans ready for the shortest path algorithm within grasshopper. I drew the short straw and ended up modeling the whole BVN floor. 

After deleting all the shit hatching lines and obstruction lines within the floor plan drawings, the shortest algorithm within the grasshopper file was able to be flow throughout the plan. 

### Grasshopper

Make sure you have the Grasshopper plug in for trialling ***shortest path*** Installed. You can find it at http://www.food4rhino.com/project/shortestwalkgh?ufh

### Bring on the Pain 

There has got to be a better way then how I did it so if you do know a better wya, please comment below. 

Basically, Anniza in her last post kind of went over the process for getting the furniture outside of the region for testing path determination within ARUPS office, so I am no going to repeat what she said. All I am doing is showing how it can be implemented into BVN instead. 

### Results 

![bvn_shortestPath]({{ site.baseurl }}/assets/bvn_shortestPath.PNG)

### Grasshopper

![Bgrasshopper_shortestPath_BVN]({{ site.baseurl }}/assets/grasshopper_shortestPath_BVN.PNG)

You can find the actual files at this dropbox link: https://drive.google.com/folderview?id=0B57wYK0849PWaVBrNXVxbGpkZDg&usp=sharing 


