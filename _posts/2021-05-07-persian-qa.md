---
toc: true
layout: post
description: First Persian Question Answering Dataset
categories: [markdown]
branch: master
image: images/persian_qa.png
comments: true
title: What I learned from Collecting PersianQA
---

# What I learned from Collecting PersianQA

This is a small but informative article for people who wish to collect new datasets in NLP (or other fields of AI).

First of all, what is PersianQA:

Persian Question Answering (PersianQA) Dataset is a reading comprehension dataset on [Persian Wikipedia](https://fa.wikipedia.org/). The crowd-sourced dataset consists of more than 9,000 entries. Each entry can be either an _impossible-to-answer_ or a question with one or more answers spanning in the passage (the _context_) from which the questioner proposed the question. Much like the `SQuAD2.0` dataset, the impossible or _unanswerable_ questions can be utilized to create a system which "knows that it doesn't know the answer". Moreover, the dataset has 900 test data available. On top of that, the very first models trained on the dataset, Transformers, are available online. All the crowd workers of the dataset are native Persian speakers. Also, it worth mentioning that the contexts are collected from all categories of the Wiki (Historical, Religious, Geography, Science, etc).

There are points that you can't find in other blog posts and nobody tells you, my goal is to not waste your time, let's get deep into it.

Here are my takeaways:

- Keep Your Raw Data Raw
  - Keeping the data raw has a lot of advantages. Raw data keeps data analysis fast and secure. Companies go through so much trouble collecting data, that it is completely illogical to start throwing away parts of it
- Never lose track of your annotators
  - You have to know which of them has annotated this particular sample.
  - We used indexing annotations for this.
- Daily Cleaning/Reporting
  - You should hire someone just to clean and report your data on a daily basis.
  - The next important things is to make it look very structured make sure that your data must eliminate or decrease the potential of Bias and Variance.
- Who are good annotators?
  - People who are aware of the purpose of this project should be put to your work
- Don't pay them early at least daily
  - You know what I'm talking about.
- Use a good tool for annotation
  - tools that can help reduce the errors and increase the speed
- Consider scaling and other versions.
  - This requires a good Structure.
  - databases, annotation tools, etc.
- Use Version Control
  - Unexpected errors always happen, so it's useful to be able to access old versions even datasets.
- Write a clear document for annotators
  - write about common mistakes and best practices
- Utilize pre-trained models as early as possible
  - with pre-trained models, you can discover your mistakes very quickly.
- Take some advice from experts
  - It's nice to have an advisor if you aren't a chief data scientist like me.
- Check out related datasets and works
  - find out if any related works and papers exist
- Working with the same annotators for a long time
  - your older annotators will be much better over time and you should save them.
  - after a while, they learn how to reduce their mistakes.

Finally, please make your dataset public, free and libre.
