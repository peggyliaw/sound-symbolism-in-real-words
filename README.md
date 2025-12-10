# sound-symbolism-in-real-words
Comparing human ratings (on [1] object shape and [2] sound shape) vs. embedding scores of shape (based on statistical co-occurrence)

### Background
Sound symbolism is the association between certain speech sounds with particular meanings. For example, words containing phonemes /l/, /m/, and /n/ are consistently judged as more round, compared to words containing phonemes /p/, /k/, and /t/. This phonomenon is known as the Bouba/Kiki effect.

Traditionally, sound symbolism has been studied using invented words. Since nonwords do not have existing meanings, the effect of sounds can be easily separated from the effect of semantic information. However, one pitfall of this approach is that the findings may have limited generalizability to real words. The dilemma here is that we cannot know for sure whether people's associations between  "moon" and round and "cactus" and spiky are based on the sounds in the words, or the shapes associated with these objects. To overcome this challenge, researchers have used real first names as experimental stimuli. First names are somewhat real and have limited semantic meanings, so they are good candidates to study sound symbolism. Despite the success in using first names, first names still do not exhibit the same significance in natural language.

### Goal
This project examines the extent to which sounds in real words contribute to their meanings, specifically shape meaning (i.e., spiky vs. round). That is, whether people's judgements of word meanings based on sounds are related to word meanings extracted from embeddings. If so, then our understanding of overall meanings of words are largely influenced by individual sounds within the words. This suggests that sound symbolism plays a significant role in word meanings. If not, then sounds of words may not have much significance in word meanings. 

Words used in this project are from Sidhu et al. (2021): https://doi.org/10.3758/s13423-021-01883-3. The words are objects in real life (e.g., necklace, pyrimid, moon, etc.)

**SoundScore** is the shape sound-symbolic score of each word, calculated based on findings in Westbury et al. (2018): https://doi.org/10.1016/j.jml.2017.09.006

**ShapeRating** is the perceived shape of the words.

### Findings
I did not find a correlation between sounds of words and shape meanings (r = -0.019, p = .416). This means that the shape associations people make based on sounds in words are not related to the actual meanings of words. 

There was a weak correlation between people's judgements on shape of objects and shape meanings (r = 0.083, p < .001). This suggests that the perceived shape of an object word is not dependent on how the object word is used along with other words in the lexicon (i.e., co-occurrences). People may use other cues to make the associations between an object and its shape (e.g., sensorimotor cues). 

The null findings in the analyses may suggest that the anchor words chosen for sound symbolism research (i.e., spiky, sharp, pointy vs. round, curved, smooth) do not reflect the shape difinitions people encounter in daily language use. 

Future research can examine whether the contribution of sounds is different between words learned early in life vs. late in life.

### Updated Findings
Two changes made to the analyses (sound_symbolism_in_real_words_Qwen3):

1. Lots of studies used Spearman correlations to compare similarities of ratings. It was proposed that Spearman is more appropriate than Pearson. Therefore, the new analysis used Spearman correlation to test associations.

2. Utilized a newer version of embedding model called Qwen/Qwen3-Embedding-0.6B: https://huggingface.co/Qwen/Qwen3-Embedding-0.6B. Qwen3 has 1024 dimensions and is a trnasformer model, compared to 300 dimensions in word2vec, which is a neural network.

With these two modifications, results changed quite a bit.

```
Combined Spearman Correlation Matrix with Word2Vec:
                      shape      SoundScore    ShapeRating
shape         1.000 (0.000)  -0.016 (0.505)  0.043 (0.070)
SoundScore   -0.016 (0.505)   1.000 (0.000)  0.213 (0.000)
ShapeRating   0.043 (0.070)   0.213 (0.000)  1.000 (0.000)
```
```
Combined Spearman Correlation Matrix with Qwen3:
                       shape     SoundScore    ShapeRating
ShapeScoreAvg  1.000 (0.000)  0.043 (0.069)  0.111 (0.000)
SoundScore     0.043 (0.069)  1.000 (0.000)  0.213 (0.000)
ShapeRating    0.111 (0.000)  0.213 (0.000)  1.000 (0.000)
```
