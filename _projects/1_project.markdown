---
layout: page
title: Real review generation using conditional generative language model
description: CSCI 566 2019 Fall Project (NLP TextGen)
img: /assets/img/12.jpg
---
**_Taejin Park, Yongwan Lim, Kaixi Wang, Yichen Zhou_**


The rise of deep neural-network based approaches have significantly improved natural dialog with machines in the past few years.
While conditional generative models have been successfully deployed in image/video applications, there is still much that can be done with GANs in text and language applications


### **Goal of this project**

The goal of this project as title indicates is to artificially generate semantically and syntactically correct sentences given human inputted keyword prompts. A possible application is fake review generation. We expect this project to have the following features:
* Generative language model (Conditional-VAE [1] and GPT-2 language model [2])
* Keyword prompts input: sentiment (rating), subject (product name), aggressiveness (vocabulary)
* Grammatically correct sentence output that contains a distinct context


### **Problem Definition**

Artificially generate semantically and syntactically correct review sentences given human inputted keyword prompts

* Training input: review sentences, rating 1~5, subject category
* Inference
    * Input: review rating 1~5, keywords (subject category,...)

    * Output: review sentences containing and/or reflecting the given distinct context 

* Environment:
    * Pytorch 0.4.1, CUDA 10.0, Cudnn 7.4

* Data:  Amazon review dataset [3]
    * Total 83.7 M reviews
    * Content: reviewer ID, product ID, product name,  star rating, review headline, review body, date, etc.
    
The main challenges of this problem would be that:
* Output is not dependent on the conditioning input.
* Quality of generated sentence (repetitive phrases, too general output) 


### **Generative Models**

* Baseline Models:
    1. Conditional Variational Auto-Encoder:

    <div class="img_row">
        <img class="col three left" src="{{ site.baseurl }}/assets/img/project1_fig_cvae1.png" alt="" title="example image"/>
    </div>
    <div class="col three caption">
        Training mode CVAE
    </div>
        
    <div class="img_row">
        <img class="col three left" src="{{ site.baseurl }}/assets/img/project1_fig_cvae2.png" alt="" title="example image"/>
    </div>
    <div class="col three caption">
        Inference mode CVAE
    </div>
    
        * Conditional VAE system that uses keyword/sentiment as conditional input.
        * Both encoder and decoder take the keyword input during training. 
        * Decoder outputs a few sentences of review about a product driven by keyword input.
        * Random noise input can work as a seed for generated review

    2. Generative Pretrained Transformer (GPT)-2 text generation model:

    <div class="img_row">
        <img class="col three left" src="{{ site.baseurl }}/assets/img/project1_fig_gpt2.png" alt="" title="example image"/>
    </div>
    <div class="col three caption">
        GPT2 Model
    </div>
    
        * A large generative, transformer-based  model ( > 1.5B parameters ) capable of conditional text generation
        * Outperforms other language models trained on specific domains without needing to be trained on the domain-specific text, and its ability to learn from raw text suggests it can benefit from unsupervised techniques
        * With fine-tuning GPT-2 on Amazon reviews, it is capable of generating long yet  realistic/coherent texts on a particular topic, product-category, or  star-rating

* Proposed Method: InfoCVAE

    <div class="img_row">
        <img class="col three left" src="{{ site.baseurl }}/assets/img/project1_fig_infovae.png" alt="" title="example image"/>
    </div>
    <div class="col three caption">
        Proposed Method: InfoVAE
    </div>


### **Experiments**

1. Data Cleaning
    * Removed very short reviews, “fake reviews” (as determined statistically by content and post date), and reviews where ratings did not correspond with the sentiment of the text 
    * Tokenization steps included  special character and stopword removal
    * Text encoding tuned to training text vocabulary using traditional NLP techniques
    * Context and input conditions (star rating, product name) are stored in input json file.
1. Model training CVAE:
    * Testing with small amount of data : less than 100K sentences
    * Conditional input is provided to encoder, decoder, and latent variable


### **Evaluation**

We will evaluate the quality of artificially generated sentences along the following two dimensions.

1. Evaluation by algorithm:
    * Employ a detector neural network model that trained separately from the generator (pre-trained GPT-2 Detector that has been fine-tuned with the same training data as the generator)
    * Statistical methods 
1. Evaluation by humans:
    * Double Blind test where evaluators are asked whether they think the text is human or machine generated
    * Artificially generated text is shuffled with human generated text. 
    * F1 score will be reported.

### **Experimental Results**

Some preliminary results from the prototype models

1. CVAE output examples: Trained on 800,000 musical instrument section comments. Star rating of 5 was given as condition for CVAE model.

    * *Example 1*<br/>
        `<sos> i have been using this for a few months now and i am very pleased with the quality of the sound . the sound is very good and the sound is very good . i have a pair of these in my studio and they are very comfortable  . <eos>`

    * *Example 2*<br/>
       `<sos> i bought this for my son for christmas . he loves it . he has a lot of fun with it  . <eos> `

    * *Example 3*<br/>
        `<sos> i love this microphone . i use it for my karaoke and it works great . i have a lot of fun with it . <eos>`

2.  GPT-2 language model examples: (unconditioned baseline)

    * *Example 1*<br/>
        `The Contour Brush is a makeup brush that features majorly angled bristles and highly curated fine-sprinkle trays. Its medium size bristles on outward strokes makes it ideal for applied color and volumizing/contour techniques. Its single-handler mode allows for easy control and produces clean product, while elegant design accentuates the product's natural beauty. The contour brush requires a firm grip on the handle, utilized to control the crooked strokes that are most desired by makeup artists.`
        
    * *Example 2*<br/>
        `Using this brush comes with a few different application techniques. First, you should apply your face powder using a straight, wide, upward stroke over the center, and play around with type of product to get the correct color. Then, use the medium type of powder brushes to apply powders to remove excess product with the downward strokes. Lastly, use the contour brush to apply the eyeshadow. Don't forget to dry the blush brush after to prevent rolling and contamination!`

    * Observations: 
        * Sampling methods have significant effects on results and intermediate training does not necessarily entail better accuracy
        * Focus on language modeling has greatest potential to increase performance
