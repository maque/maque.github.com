---
layout: post
title:  "Tunel Effect - First Attempt"
date:   2016-03-11
categories: demoscene
tags:
- dajsiepoznac
- demoscene
---

So finally I did my own tunel effect and I'm quite happy about it. 
It's simple, it's not perfect, but it's mine :)

So lets back to thinking about tunel. What do we acctually need?

* Texture - that we have from roto zoom effect (x xor y)*
* Scaling from the center to the edges *

Remember how to scale texture? Just draw each pixel as many times as much you want to scale.
So if we want to have big texture at the edges of scene, then we need to divide X coordinate by distance from the center.

Let's do some psuedo code:

{% highlight javascript %}
var distance = Math.sqrt(Math.pow(center_x,2)+Math.pow(center_y,2))+1; //distance from the center will use for X of Texture

//shiftX/Y is just for little animation for each frame
var xsize = Math.floor((x*ratio/distance)+shiftX)%width;
var ysize = Math.floor((y*ratio/distance)+shiftY)%height;  

var color = texture[ysize][xsize];
          
_Screen.SetPixel(x,y,ColorPalette[color]);  
{% endhighlight %}
[full code](https://github.com/maque/JSDemoScene/blob/master/Tunel/effect.js){:target="_blank"}

And now, presentation:
{% include tunel.html %}