---
layout: post
title: Work with time
date: 2016-08-18 11:00:00
type: post
published: true
status: publish
categories: []
tags: []
description: Time as a variable and effective communication
# 110 marker 1234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789
twitter-body: you write here and it goes on the share for twitter
featuredimg: polar-bear.jpg #if you put an image here it goes on twitter too

author: tiara
---

In Einstein's theory of relativity time is a literal fourth dimension of spacetime in the sense that spacetime has a natural distance measure that blends time and the three dimensions of space. 

<p><a href="https://commons.wikimedia.org/wiki/File:8-cell-simple.gif#/media/File:8-cell-simple.gif"><img src="https://upload.wikimedia.org/wikipedia/commons/5/55/8-cell-simple.gif" alt="8-cell-simple.gif"></a><br> Check out 3D projection of a tesseract undergoing a simple rotation in four dimensional By <a href="https://en.wikipedia.org/wiki/User:JasonHise" class="extiw" title="wikipedia:User:JasonHise">JasonHise</a> at <a href="https://en.wikipedia.org/wiki/" class="extiw" title="wikipedia:">English Wikipedia</a></p>

In plain words, time is a human construct used to determine change. For many, time appears to 'stand still' when nothing happens. Understanding and approaching the variable of time has alot to do with what I assume is an potential face-to-face interactions. 

### Very quickly...what is a potential for interaction 

<b> Here I want to make a clear destinction between what I say is a interaction and what is a potential for interaction. A potential for interactions is what I use to assume someone is having an interaction but do not know for sure, which will have to be the case in my thesis(as it will be an automated approach to tracking interactions). Interactions on the other hand is something that can be more subjective and knowing for sure if someone has interacted with someone else is hard for a computer to do</b>


### Defining time: Segments

For example 30 second intervals as 'Segements' (and I'll come back to this with a later post) but essentially it is dividing up the program into) as a indication of moments in Time. In response to experiment 8, we realised we needed to take the average a period of time in order to get a better indication of the rssi (because of its fluxuation). see 'early work using time' as to how I plan to do this. 

### Representation of time 

1. Animation: This animation moves at 10 frames per second.

<p><a href="https://commons.wikimedia.org/wiki/File:Animexample.gif#/media/File:Animexample.gif"><img src="https://upload.wikimedia.org/wikipedia/commons/a/a4/Animexample.gif" alt="Animexample.gif"></a></p>

Animation is the process of making the illusion of motion and change by means of the rapid display of a sequence of static images that minimally differ from each other (according to wikipedia) 

PROBLEMS: grabbing a segment of that data and analysing it

2. Static images: The bouncing ball animation (below) consists of these six frames.

![something or other]({{ site.baseurl }}/assets/time/static_images.png)

PROBLEMS: Conveying motion is disjointed 

### Early work using time

Below is a sample of json time and rssi values used as imputs for producing time segments. The difference between one state to another can be anything between milliseconds, to 30 second intervals(which is the case in this example)

~~~ bash 

{ "time" : "2016-07-12T09:52:30.021353" , "rssi" : -61 },
{ "time" : "2016-07-12T09:52:31.852827" , "rssi" : -69 },
{ "time" : "2016-07-12T09:52:32.893738" , "rssi" : -61 },
{ "time" : "2016-07-12T09:52:33.852827" , "rssi" : -73 },
{ "time" : "2016-07-12T09:52:34.893738" , "rssi" : -76 },
{ "time" : "2016-07-12T09:52:35.117117" , "rssi" : -69 },
{ "time" : "2016-07-12T09:52:36.344178" , "rssi" : -78 },
{ "time" : "2016-07-12T09:52:37.117117" , "rssi" : -65 },
{ "time" : "2016-07-12T09:52:38.344178" , "rssi" : -69 },
{ "time" : "2016-07-12T09:52:39.021353" , "rssi" : -70 },

~~~


The first step was importing the json file into the grasshopper script so the python can read the file. Was simple enough:

![something or other]({{ site.baseurl }}/assets/time/time_import.png) 


### Cull Index 

The next step was not really necessary but helpful to sort all the low rssi detections from the most useful higher rssi values. 

![something or other]({{ site.baseurl }}/assets/time/cull_low_rssi.png) 



### Average all detections within a 30 second time period 

![something or other]({{ site.baseurl }}/assets/time/average_rssi.png) 

~~~ Bash

import Rhino
import scriptcontext
import datetime

~~~

Find me the index that is >= to the time difference of the first index

~~~ bash 

def StringToDateTime(string):
    return datetime.datetime.strptime(string, '%Y-%m-%dT%H:%M:%S.%f')# the GH needs the formatting for the new datetime

~~~ 

Take the datetime and then reformat it/ understand it based on this datetime translation key: %Y-%m-%dT%H:%M:%S.%f 

~~~ Bash

   times = [StringToDateTime(time) for time in timeList] 
   rssi = rssiList
   instance = 0
   firstTime = times[0]
   currentTimePeriodEnd = firstTime + datetime.timedelta(0,timeDifference)
   avgList = []

chunk = []

~~~ 

Input is a list of strings (for whatever reason) so convert them to a datetime,  while the index of f is within the range of rssiList, do something

~~~ bash 

for index, time in enumerate(times):
    # emumerate(takes a number of things(within a range) and mentions them one by one. This was used to gather all detections within a time period which is then sent to be averaged. 
    if time <= currentTimePeriodEnd:
        chunk.append(int(rssi[index])) # the input is a list of strings for what ever reason so convert to int.
    else:
        avg = sum(chunk)/len(chunk)
        avgList.append(avg)
        chunk = []
        currentTimePeriodEnd = currentTimePeriodEnd + datetime.timedelta(0,timeDifference)
~~~ 

Now take the first time period and then the last time period(plus 30 seconds) and then average all the detections within that time period. 




