---
layout: page
title: Real review generation using conditional generative language model
description: CSCI 566 2019 Fall Project (NLP TextGen)
img: /assets/img/12.jpg
---

<!--![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)-->

### **Goal**

The goal of this project as title indicates is to artificially generate semantically and syntactically correct sentences given human inputted keyword prompts. A possible application is fake review generation. We expect this project to have the following features:
* Generative language model (Conditional-VAE [1] and GPT-2 language model [2])
* Keyword prompts input: sentiment (rating), subject (product name), aggressiveness (vocabulary)
* Grammatically correct sentence output that contains a distinct context

<div class="img_row">
<img class="col three left" src="{{ site.baseurl }}/assets/img/project1_fig1.png" alt="" title="example image"/>
</div>
<div class="col three caption">
This image can also have a caption. It's like magic.
</div>

### **Motivation**

The rise of deep neural-network based approaches have significantly improved natural dialog with machines in the past few years.
While conditional generative models have been successfully deployed in image/video applications, there is still much that can be done with GANs in text and language applications
