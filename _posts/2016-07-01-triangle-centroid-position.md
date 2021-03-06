---
layout: post
title: Positions, triangles and centroids
date: 2016-07-01 0:00:00
type: post
published: true
status: publish
categories: []
tags: []
description: Centroid-triangulation method for locating a person indoors
# 110 marker 1234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789
twitter-body: you write here and it goes on the share for twitter
featuredimg: polar-bear.jpg #if you put an image here it goes on twitter too

author: tiara
---

Since the RSSi is not really giving a clear indication of an accurate proximity of a person, for example, in this image(credits to Annisa for drawing the graph), Rssi at 0m is the same as it is at 4m, we need another way of determining where a person is within a space. 

![shitty rssi]({{ site.baseurl }}/assets/shitty-rssi.PNG)

So I began playing with some ideas of triangulation.  A traditional mode is explained in the diagram below, however the lengths(described by the lines within the triangle) are almost impossible to accurately determine based on the RSSi values) as explained above. 

![triangle centroid]({{ site.baseurl }}/assets/normal-triangulation.PNG)


So my thoughts are to use a modified version of a triangulation formula, but using an area/centroid calculation to find the point. 

![triangle centroid]({{ site.baseurl }}/assets/centroid-triangle.PNG)

Using the last known three baseStations and their known distances apart, we can map where the person is by the centroid and the exclusion of the furniture, The results would look a little like this. The Blue dots represent the location of the three nearest base stations to the received broad casted BLE by the estimote sticker(or whatever we end up using). The red is the actual position of the individual/centroid of the triangle, for an example. 

![triangle centroid]({{ site.baseurl }}/assets/trinagle-centroid.PNG)

The potential issue with this, however is 1) determining which BaseStations are the closest, and 2) differentiate between one path way and another. For example, the triangle may form at an opposite position form where it actually is. I hope to do some mock testing next week to test the veracity of this method. 

### Moving forward

The next step here is to create a grasshopper script which can do this: Find the last three points(closest points) to a position) and then create a triangle where its area is then asked to find the centroid and compare how accurate the results are(pretty much what the image above does). I'll mock something up over the weekend. 
