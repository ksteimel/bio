---

title: Research Activities Spring 2018
layout: default

---

- I am working on integrating distantly supervised sentiment tweets into irony/sarcasm detection for tweets.
  - Previous results that I've obtained have shown that the MPQA lexicon improved results during cross validation scoring on the training dataset 
  - However, the test dataset did not appear to benefit from the introduction of the MPQA data.
  - My general intuition is that the words included in the MPQA lexicon were not twitter specific enough and thus were not very likely to occur
  - If these words are informative (with regards to irony detection) but not prevalent, they aren't particularly useful.
    - e.g. even though 'distraught' is strongly negative, it probably does not occur in data derived from tweets. if it does, it probably occurs with such low frequency that it is not useful when applied to unseen data.
  - My goal is to apply this to a large bank of tweets I've collected with distantly supervised sentiment labels. Then, I can use this to extract words that typically occur with negative sentiment and words that occur with positive sentiment to generate my own sentiment lexicon that has twitter specific vocabulary. 
  - Previous work by others (note to self: look this up in the future) has shown that sentiment specific word embeddings extracted from a Convolutional Neural Network work well for sentiment tasks, perhaps these would be beneficial for irony/sarcasm detection tasks

- I am also working on part of speech tagging for Luyia languages. Right now I'm trying to figure out which language pairs make the most sense for source--target lineups. I have Bukusu, Wanga, and Tiriki data right now with the majority being Wanga data. However, I need to pick pairs that are interesting for genetic relatedness reasons. 
