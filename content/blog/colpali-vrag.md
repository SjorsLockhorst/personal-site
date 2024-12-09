---
title: "V-RAG with ColPali. Is it feasible?"
description: 'Could we skip parsing and chunking of PDFs, and just use a VLM directly?'
path: /blog/colpali-vrag
date: 2024-12-5
category: AI
ogImage:
  component: BlogPost
  props:
    readingMins: 4
sitemap:
  loc: /blog/colipali-vrag
---

## RAG without parsing and chunking?

That is the promise of using Vision Language Models (VLMs) directly to embed PDFs. 
Instead of having to do Optical Character Recognition (OCR), followed by cleaning, chunking and embedding, we could just embed pages of a PDF as images with a VLM.
This is the promise of [ColPali](https://arxiv.org/abs/2407.01449).

![ColPali vs standard retrieval](/images/blog/colpali-vrag/colipali-pipeline.png)
*Standard way of doing RAG vs. [ColPali](https://arxiv.org/abs/2407.01449)'s proposed method*

But how can a language model even 'see'? For that, we take a brief dive into the history of VLMs.

## A brief history of VLMs

### Vision Transformer (ViT)
For the longest time, Convolutional Neural Networks (CNNs) were the state of the art when it came to several computer vision tasks, such as classification or object detection.
In the meanwhile, the NLP field was forever changed by the publishing of the [transformer paper](https://arxiv.org/abs/1706.03762) in 2017.
In 2021, the Google Research team came out with the pivotal [paper](https://arxiv.org/abs/2010.11929): "An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale". 
In this paper, they apply the transformer architecture image classification.

![Visual Transformer (ViT) architecture](/images/blog/colpali-vrag/vit.png)

*The architecture of the Vision Transformer (ViT)*

They do this by dividing images into equally sized patches, flattening each patch, and linearly embedding them. 
This process loses spatial information since we're squishing the patches from 2D to 1D.
This information gets encoded back with position embeddings. Interestingly the authors find that 1D position embeddings are performant enough for the task when compared to more complex 2D position embeddings.
They also prepend a learnable embedding `[class]`, which serves as a representation of the entire image.

Then, the embeddings go into a transformer encoder, just like they would for text.
To classify the image, they add a Multi Layer Perceptron (MLP) to the last hidden state of the `[class]` token, which finally classifies the image.

### Unifying images and text

All good and well that we can use the same architecture for image and text, but how can we get one model to understand both modalities?
This is what CLIP proposed to do.


## Benefits

## Drawbacks

## An experiment






