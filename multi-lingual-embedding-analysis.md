# Which Model (LASER, mBERT, XLMR, Sentence Transformer) to choose for Multilingual Embedding ?

![](https://miro.medium.com/fit/c/96/96/0*L3v9OPLeOu9v1IgK.)

![](https://miro.medium.com/max/60/1*8yB8C5Y2b_sD5Ikdz4_wFQ.png?q=20)

![]()

![](https://miro.medium.com/max/1208/1*8yB8C5Y2b_sD5Ikdz4_wFQ.png)

> Question to Audience — THINK

**Question to Audience — THINK**

Multi-lingual embedding learn representations in joint space. It means that these embedding share common vector space.

So, if we take same sentence in multiple languages and compute similarity say cosine similarity between them, it should come really high or if we plot vector of same sentence in multiple languages on 2-dimensional space, it should come near to each other.

Can we make this as our basis to find which multi-lingual embedding E ∈ {LASER, mBERT, XLMR, Sentence Transformer} give best and stable [cosine similarity](https://www.machinelearningplus.com/nlp/cosine-similarity/). High and stable similarity indicates that Multi-lingual embedding is good.

Example — If we translate *“how are you ?”* in french language using google translator, translation comes out *“Comment allez-vous ?”*. Which Embedding among E gives best and stable similarity ?

I hope after looking through Image-1, you may have question Is XLMR best ? Nooo !!, LASER ?? or Sentence Transformer ?

Lets Explore this below in article !!

> STEP — 01: Data preparation & Language Scope

**STEP — 01: Data preparation & Language Scope**

Language used for analysis: English — en, German — de, Spanish — es, French — fr.

For quick analysis, taking two data set for each language pair (total 6 language pair: en-fr, en-de, en-es, de-fr, de-es, fr-es)

* **Similar sentence language pair**: Taken 14 different sentences in english and translated in to other 3 languages i.e. we have now 14 different sentence for each language pair. Say for en-fr, will have 14 different sentence pair (sentence_english, sentence_french).

![](https://miro.medium.com/max/60/1*X5uxw1Y4UUTSiyNhqvGFxw.png?q=20)

![]()

![](https://miro.medium.com/max/2510/1*X5uxw1Y4UUTSiyNhqvGFxw.png)

* **Dissimilar sentence language pair: **Taken 14 different sentences, sentence for each language pair is also different i.e for language pair es-fr, same sentences is not used in spanish and french.

![](https://miro.medium.com/max/60/1*9br6SN2NlfZa1nQPN_DFaQ.png?q=20)

![]()

![](https://miro.medium.com/max/2524/1*9br6SN2NlfZa1nQPN_DFaQ.png)

> STEP — 02: Get Embedding of text

**STEP — 02: Get Embedding of text**

For analysis, we are using four pre-trained multi-lingual embedding (LASER, mBERT, XLMR, Sentence Transformer).

For each multi-lingual embedding say LASER, get embedding of text (similar and dis-similar dataset) for all four languages i.e. will have 4 columns (LASER_EN,LASER_ES, LASER_DE, LASER_FR). Similarly, will have 4 columns for remaining 3 multi-lingual embedding i.e. in total 16 columns (4 Multi-lingual embedding X 4 Language).

![](https://miro.medium.com/max/60/1*zYbAhX3GC_lLKlOGWdFABQ.png?q=20)

![]()

![](https://miro.medium.com/max/540/1*zYbAhX3GC_lLKlOGWdFABQ.png)

> STEP — 03: Visualization of Multi-lingual Embedding

**STEP — 03: Visualization of Multi-lingual Embedding**

To validate perfromance of multi-lingual embedding, Plot embedding of same sentence from multiple language and check below two points:

* Are we getting cluster for same sentence in multiple languages ?
* Are these clusters separable enough for all different sentences ?

![](https://miro.medium.com/max/60/1*mXGsNEK6nvvG8sQNyYCl_w.jpeg?q=20)

![]()

![](https://miro.medium.com/max/1728/1*mXGsNEK6nvvG8sQNyYCl_w.jpeg)

**Observation:**

* Getting very clear cluster for sentence transformer and for LASER up to some extent.
* For XLMR and mBERT, instead of getting cluster at sentence level, getting cluster at langauge level which isn’t good sign for Multi-lingual embedding. Whole point of multi-lingual embedding is that its embedding don’t distinguish between languages, it share common vector space.

> STEP — 04: Find Cosine Similarity

**STEP — 04: Find Cosine Similarity**

Cosine similarity between two vectors give value of range -1 to +1, it tells similarity between two vectors. High value (towards +1) confirms vector are similar.

![](https://miro.medium.com/max/60/0*DDdwHT845BYprhvr.png?q=20)

![]()

![](https://miro.medium.com/max/540/0*DDdwHT845BYprhvr.png)

In our case, vector will be embeddings for different languages i.e. Cosine similarity between <sentence_en, sentence_fr>.

> STEP — 05: Analysis/Comparison of Multi-lingual Embedding per Language Pair using Cosine Similarity

**STEP — 05: Analysis/Comparison of Multi-lingual Embedding per Language Pair using Cosine Similarity**

To validate performance of multi-lingual embedding, lets check one more important point which will double confirm our visualization part:

* Are we getting **high** cosine similarity score for **similar** sentence language pair data (E.g. cosine <sentence_en,sentence_fr>~ +1) and **less** cosine similarity score for **dis-similar** sentence language pair data (E.g. cosine <sentence_en,sentence_fr>~ -1) ?

Ideally, average difference of cosine similarity of similar and dis-similar data should be high i.e. largely separable.

![](https://miro.medium.com/max/60/1*wf62ikw_oplP2HL8qcFt7A.png?q=20)

![]()

![](https://miro.medium.com/max/2328/1*wf62ikw_oplP2HL8qcFt7A.png)

**Observation:**

* Average difference of cosine similarity of similar and dis-similar data is good and highest for Sentence Transformer and LASER. It indicates that Sentence Transformer and LASER working quite good relative to mBERT and XLMR.

> STEP — 06: Conclusion

**STEP — 06: Conclusion**

* Ideally, Mult-lingual embedding share common vector space.
* Both step-3 (Visualization) and step-5 (Cosine similarity Analysis) confirms Sentence Transformer and LASER outperforms and it should be ideal choice for multi-lingual embeddings at sentence level.

**Written by: **Joint efforts by [Aakash Goel](https://medium.com/u/5201449dcac2?source=post_page-----bf9589b38a31----------------------), [Ashu Agrawal](https://medium.com/u/baef9f185116?source=post_page-----bf9589b38a31----------------------).

Now, you are ready to clap :) and please share with your friends as well.

Thanks !!