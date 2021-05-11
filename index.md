---
title: Topic Sentence Extraction
# subtitle: This is the demo site for Bulma Clean Theme
layout: page
# callouts: home_callouts
show_sidebar: false
hero_link: https://github.com/TopicSentenceExtraction/topicsentenceextraction
hero_link_text: Github Repository
---

## Introduction
Topic sentence is one of the crucial parts for readers in article reading for many reasons. It summarizes the main idea of a body paragraph to show the big picture of a writer's idea to readers. Other than being a mere summary, topic sentence also serves as a sub-thesis of an article which is general enough to cover the support in the rest of body paragraph while being more direct than the thesis of the whole article[1]. Hence, finding a way to summarize the paragraph with a grammatical sentence will be very helpful for readers to recognize the main idea much easier in a short period of time.

Our goal is to build a topic sentence generation tool. This tool receives a body paragraph as the input then returns a summary sentence as the output. The dataset that we are going to use is [arXiv Dataset](https://www.kaggle.com/Cornell-University/arxiv) from Kaggle which includes millions of paper metadata in json format. Our team uses [T5(Text-to-Text Transfer Transformer)](https://huggingface.co/transformers/model_doc/t5.html) for model traning and [BLEU score](https://en.wikipedia.org/wiki/BLEU) for model evaluation.

## Methodologies

### Dataset Sample
```javascript
{
  "id": "0704.0001",
  "submitter": "Pavel Nadolsky",
  "authors": "C. Bal\\'azs, E. L. Berger, P. M. Nadolsky, C.-P. Yuan",
  "title": "Calculation of prompt diphoton production cross sections at Tevatron and\n  LHC energies",
  "comments": "37 pages, 15 figures; published version",
  "journal-ref": "Phys.Rev.D76:013009,2007",
  "doi": "10.1103/PhysRevD.76.013009",
  "report-no": "ANL-HEP-PR-07-12",
  "categories": "hep-ph",
  "license": null,
  "abstract": "  A fully differential calculation in perturbative quantum chromodynamics is\npresented for the production of massive photon pairs at hadron colliders. All\nnext-to-leading order perturbative contributions from quark-antiquark,\ngluon-(anti)quark, and gluon-gluon subprocesses are included, as well as\nall-orders resummation of initial-state gluon radiation valid at\nnext-to-next-to-leading logarithmic accuracy. The region of phase space is\nspecified in which the calculation is most reliable. Good agreement is\ndemonstrated with data from the Fermilab Tevatron, and predictions are made for\nmore detailed tests with CDF and DO data. Predictions are shown for\ndistributions of diphoton pairs produced at the energy of the Large Hadron\nCollider (LHC). Distributions of the diphoton pairs from the decay of a Higgs\nboson are contrasted with those produced from QCD processes at the LHC, showing\nthat enhanced sensitivity to the signal can be obtained with judicious\nselection of events.\n",
  "versions": [...],
  "update_date": "2008-11-26",
  "authors_parsed": [...]
}
```

### T5 Model

### BLEU 
BLEU(bilingual evaluation understudy) is an algorithm for evaluating the quality of translation by using machine from one language to another.[] It can also be used to compare the similarity between two sentences. That is, the algorithm compute the n-gram overlap between the candidate sentence and multiple reference sentences from corpus with brevity penalty which is used for lowering the score properly when the candidate sentence is too short compared to the closest reference.[] By using the BLEU, we can evaluate the accuracy of the extracted topic sentences by comparing them to actural titles.

## References
1. [Wikipedia: Topic Sentence](https://en.wikipedia.org/wiki/Topic_sentence)
2. [Wikipedia: BLEU](https://en.wikipedia.org/wiki/BLEU)
3. [Evaluating models](https://cloud.google.com/translate/automl/docs/evaluate#bleu)