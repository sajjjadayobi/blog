---
toc: true
layout: post
description: This is what I have found out
categories: [markdown]
branch: master
image: images/persian_qa.png
comments: true
title: I was confused about AdamW and Adam + Warm Up 
---

# I was confused about AdamW and Adam + Warm Up 

This is what I have found out

## Warm Up is a learning Rate Scheduler

Warm up steps are just a few updates with low learning rate at the beginning of training. After this **warm up**, you use the regular learning rate (schedule) to train your model to convergence.

The idea that this helps your network to slowly adapt to the data intuitively makes sense. However, theoretically, the main reason for warm up steps is to allow adaptive optimizers (e.g. Adam, RMSProp, ...) to compute correct statistics of the gradients. Therefore, a warm up period makes little sense when training with plain SGD.

If your data set is highly differentiated, you can suffer from a sort of "early over-fitting". If your shuffled data happens to include a cluster of related, strongly-featured observations, your model's initial training can skew badly toward those features -- or worse, toward incidental features that aren't truly related to the topic at all.

Warm-up is a way to reduce the primacy effect of the early training examples. Without it, you may need to run a few extra epochs to get the convergence desired, as the model un-trains those early superstitions.

Many models afford this as a command-line option. The learning rate is increased linearly over the warm-up period. If the target learning rate is `p` and the warm-up period is `n`, then the first batch iteration uses `1*p/n` for its learning rate; the second uses `2*p/n`, and so on: iteration `i` uses `i*p/n`, until we hit the nominal rate at iteration `n`. this means that the first iteration gets only 1/n of the primacy effect. This does a reasonable job of balancing that influence. for example Bert use liner Warm Up with linear decay /\

## AdamW is Adam with correct Weight Decay

In general, Adam needs more regularization than SGD, L2 and weight decay are the same in just Vanilla SGD, not in algorithms that use momentum. Weight decay is just in backward pass and added to the gradients but L2 add directly in loss function
[AdamW](https://arxiv.org/abs/1711.05101) paper shows that weight decay work better in the case of Adam, but the implementation of Adam with weight decay was wrong during these years. in this paper, they fixed it.  

- **W** stands for weight decay

```python
optimizer = torch.optim.AdamW(net.parameters(), lr=0.001, weight_decay=0.01)
```

When weight decay is 0, there is no difference between Adam and AdamW.
