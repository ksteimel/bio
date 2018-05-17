---

title: Part-of-Speech tagging in Wanga
layout: default
category: cl

---

I have my first results from using an SVM tagger on Wanga data extracted from the fieldworks corpus. They're quite good. With only 1500 wanga words, noun class identification reaches 95.4 f-score while doubling the number  of tokens nets another percent. 

pos tagging gets an f-score of 90.7 out of the gate for the smaller training size and around 94 for the larger dataset. 

Unfortunately, this doesn't leave much room for the Swahili data to contribute but the fact that the performance does improve as the training dataset gets larger is encouraging. 

Now to work on the markov models
