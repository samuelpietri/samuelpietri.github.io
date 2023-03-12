---
layout: distill_custom
title:  "Deep Image Matting"
excerpt: "Deep Learning solutions for Image Matting"
date:   2021-01-02 16:28:53 +0100
categories: deep-learning image-matting
classes: wide 
header:
  teaser: "assets/images/002_image_matting/test.png"
  #overlay_image: "assets/images/002_image_matting/test.png"

toc:
  - name: MODnet Results
    # if a section has subsections, you can add them as follows:
    # subsections:
    #   - name: Example Child Subsection 1
    #   - name: Example Child Subsection 2
  - name: U-2-Net Results
---
 <br />

The greenscreen will become obsolete, that's a fact. One way or another new techniques will jump in and will make work of image-matting a much more automated, less time-consuming job. To be fair some alternatives are already been used in Hollywood productions such as the [virtual sets](https://www.insider.com/green-screen-virtual-sets-mandalorian-2020-4) used in the latest Disney series *The Mandalorian*. A set of led screens recreate the environment in real time improving the effects of reflections and allowing the actors to move in a much more realistic set are becoming a thing. 

Deep learning techniques are emerging as well, letting the practice of manually cutting out content over background becoming fully automated, with almost no supervision. Now I'll take a look at a couple of different projects I found.

- **[MODNet](https://github.com/ZHKKKe/MODNet) -** *Is a Green Screen Really Necessary for Real-Time Portrait Matting?*
- **[U-2-Net](https://github.com/NathanUA/U-2-Net)** *- Going Deeper with Nested U-Structure for Salient Object Detection*

Although they have fairly different architectures they do share the common great advantage to be very easy to test and flexible enough to be tested quickly on different content. *U-2-Net* has shown already very interesting application capabilites. Just look at the [AR Copy Paste](https://github.com/cyrildiagne/ar-cutpaste) project from Cyril Diagne which is just scratching the surface of how these new tools will gradually change the content creation field.

The possible applications of this technique are fairly straightforward and apart from background matting for movies, we see a vast usage of similar tools in our daily life for any video conferencing system at our disposal. Who doesn't want some custom, weirdly-looking background these days? To be fair there are other promising projects such as [Real-Time High-Resolution Background Matting](https://github.com/PeterL1n/BackgroundMattingV2) which can give very similar or even better results but most of them are trickier to work with, require auxiliary inputs or they're simply computationally intensive.

Since I've already introduced *The Mandalorian* I'll use some shots from the series to test both frameworks. I'll start with these scene, with one or multiple character and different lighting conditions.

 <br />

## MODNet results
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html  path="assets/img/posts/image_matting/MODNet_001.jpg" class="img-fluid rounded" %}
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html  path="assets/img/posts/image_matting/MODNet_002.jpg" class="img-fluid rounded" %}
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html  path="assets/img/posts/image_matting/MODNet_003.jpg" class="img-fluid rounded" %}
    </div>
</div>

 <br />

## U-2-Net results
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html  path="assets/img/posts/image_matting/U-2-Net_001.jpg" class="img-fluid rounded" %}
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html  path="assets/img/posts/image_matting/U-2-Net_002.jpg" class="img-fluid rounded" %}
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html  path="assets/img/posts/image_matting/U-2-Net_003.jpg" class="img-fluid rounded" %}
    </div>
</div>
 <br />
I believe they're doing a decent job extracting the foreground characters from the environment but anyone who has tried cutting out figures in Photoshop knows that the real issue arise when your working on the edges of the character. Any little detail, the hair or even accessories can be troublesome and greatly affect the ability to perform the task well.
The *MODNet* model seems to handle very well a wider range of scenarios and is able to extract details in more refined way, expecially on the boundary of the extracted shape. The *U-2-Net* is still very good but less precise on the border and the objects direcly related to the character.

It becomes clear that having really detailed masks such the one produced by the *MODNet* model, can be used right away letting you change the background in a metter of seconds such in this small sample I provide here below.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html  path="/assets/img/posts/image_matting/Image_Matting_Test.gif" class="img-fluid rounded" %}
    </div>

</div>

Let's move to video content. Here I selected scenes with clear characters in front of the camera. 

<iframe src="https://player.vimeo.com/video/496647965" width="100%" height="450" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

And surpsingly both models are doing just fine. The time consistency is still the main issue though, with some clear unwanted flickering effect appearing on the alpha mask especially with fast movement on screen.

After some test it becomes clear that *MODNet* sometimes show these large stains, which are difficult to intepret since they seems to appear with different contents in the input image.
 <br />


<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html  path="/assets/img/posts/image_matting/MODnet_Errors.jpg" class="img-fluid rounded"%}
    </div>
</div>


 _MODnet_Errors_
 <br />

*U-2-Net* on the other hand is not showing any weird shapes in the alpha mask but at the same time is less precise finding the actual contour of the characters and it definitely struggles handling reflections, such us the one on the armour.
 <br />

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html  path="/assets/img/posts/image_matting/U-2-Net_Errors.jpg" class="img-fluid rounded"%}
    </div>
</div>
_U-2-Net_Errors_
<br />

Here some more side by side comparison between the two models. Again they both have their flaws but in the context of portrait matting I believe *MODNet* is doing a better job. 
<br />

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html  path="/assets/img/posts/image_matting/MODNet_U-2-Net_001.jpg" class="img-fluid rounded"%}
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html  path="/assets/img/posts/image_matting/MODNet_U-2-Net_002.jpg" class="img-fluid rounded"%}
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html  path="/assets/img/posts/image_matting/MODNet_U-2-Net_003.jpg" class="img-fluid rounded"%}
    </div>
</div>

 <br />

And if you haven't had enough here's a longer footage where a much diverse of images are processed. The more we have 
<iframe src="https://player.vimeo.com/video/496656226" width="800" height="450" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>
 <br />

Next up some I'll do some more testing of these models in the wild.