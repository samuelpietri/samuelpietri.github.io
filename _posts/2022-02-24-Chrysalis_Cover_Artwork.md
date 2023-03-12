---
layout: distill_custom
title:  "Chrysalis cover artwork"
description: "Behind the creation of the artwork"
date:   2020-12-24 16:28:53 +0100
categories: deep-learning depth-estimation
classes: wide
header:
  teaser: ""
  #overlay_image: "assets/images/001_depth/milan_depth.gif"
authors:
  - name: Samuel Pietri

toc:
  - name: Intro
    # if a section has subsections, you can add them as follows:
    # subsections:
    #   - name: Example Child Subsection 1
    #   - name: Example Child Subsection 2
  - name: Process
  - name: Result
---
# Intro
When I first started working on the album cover for Chrysalis I started tinkering with some of the major underlying themes the album is following which is the life of the butterfly. Although this aspect is actually used as an opportunity to tell a personal and introspective story, it remained interesting to use elements that graphically resembled butterflies to give the first visual taste of the work.
From the beginning I took into consideration the idea of ​​using only generative-AI based methods for the realization of the artwork and consequently I exploited my experience in using [GAN](https://en.wikipedia.org/wiki/Generative_adversarial_network) to create new visual material starting from butterfly photographs. 
<figure>
    <img src="/assets/img/posts/chrysalis_cover/butterfly.jpg">
</figure>
# Process
For this first step I prepared a dataset using creative commons images of macro photographs from flickr and trained a modified version of [Stylegan2](https://github.com/NVlabs/stylegan2). The images have been scraped and pre-processed in order to use the model fine-tuning the weight from the stylegan2-ffhq trained model.
Here's a small excerpt of the outcome.
<figure>
    <img src="/assets/img/posts/chrysalis_cover/butterfly_gan_001.gif">
</figure>

At this point I realized that my main interest was in butterfly wing textures and that I needed a different dataset to be able to explore these patterns more. In this sense I then used the images I found on the [data portal of the Natural History Museum](https://data.nhm.ac.uk/dataset/collection-specimens/resource/05ff2255-c38a-40c9-b657-4ccb55ab2feb?view_id=6ba121d1-da26-4ee1-81fa-7da11e68f68e&filters=project%3Apapilionoidea+new+types+digitisation+project) and I used some techniques proposed by [marian42](https://github.com/marian42/butterflies) to be able to scrape and process these images.
In particular, it was necessary to crop the available images, align them and separate the background from the animal with a mask.
Once these operations have been carried out, I repeated the training process.

<figure>
    <img src="/assets/img/posts/chrysalis_cover/butterfly_dataset.jpg">
    <figcaption>Example of one of the images from the Natural History Museum dataset</figcaption>
</figure>

Also in this case the main theme remained the butterfly in its entirety and every transformation of the pigments took place bringing with it other morphological variations superfluous for my interest. I then edited and pre-processed the images with smaller crops focusing only and exclusively on the internal parts of the wings.

<figure>
    <img src="/assets/img/posts/chrysalis_cover/butterfly_collage_001.jpg">
    <figcaption>CVDE monocular depth estimation</figcaption>
</figure>

<figure>
    <img src="/assets/img/posts/chrysalis_cover/butterfly_collage_002.jpg">
    <figcaption>CVDE monocular depth estimation</figcaption>
</figure>

The result of the process allowed me to explore this generative content in a free way, enhancing some artifacts that emerged in the training process of the neural network.
To evaluate the generation of formats that will go beyond that of the trained model, I used some [eps696](https://github.com/eps696/stylegan2) techniques in its implementations that allow you to generate images with dimensions and aspect-ratio at will.

<figure>
    <img src="/assets/img/posts/chrysalis_cover/butterfly_gan_002.gif">
</figure>

<figure>
    <img src="/assets/img/posts/chrysalis_cover/Chrysalis_Cover_0001.jpg">
</figure>

<figure>
    <img src="/assets/img/posts/chrysalis_cover/Chrysalis_Cover_0003.jpg">
</figure>

I then generated a few thousands images with variable parameters in order to evaluate different directions and possibilities.
<figure>
    <img src="/assets/img/posts/chrysalis_cover/butterfly_collage_003.jpg">
</figure>
# Result
After a few session with Riccardo Bazzoni, the album's author, we concurred on the final direction for the artwork and selected some of the samples for the final post-process phase. Very slight modification on textures and composition were then applied and here you can see the final result.
<figure>
    <img src="/assets/img/projects/Chrysalis_Cover/Chrysalis_Artwork.jpg">
    <figcaption>Final Album cover</figcaption>
</figure>

