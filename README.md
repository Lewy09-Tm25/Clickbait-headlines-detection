# Clickbait-headlines-detection

## Motivation
There is an overwhelming amount of news information available online. Some news headlines
are known as clickbait – they aim to attract users to click on a link but the articles that they link
to may not be of value or interest to the reader. In this project we aim to answer the following
question: Can we automatically distinguish between clickbait and non-clickbait headlines, using
a variety of linguistic cues?
## Data
You are provided with a corpus of clickbait and non-clickbait article headlines. The corpus is described in detail in this paper: https://arxiv.org/pdf/1610.09786.pdf
## Approach
Using the NLTK library, the important aspects of linguistic cues have been extracted from the text corpus. These features played a pivotal role in classifying the headlines. The model used here was Naive Bayes algorithm. Below are the features used to train the dataset:-
1. Stop words: counts for each function word (from the NLTK stopwords list)
2. Syntactic: counts for the following 10 common POS tags -- ['NN', 'NNP', 'DT', 'IN', 'JJ',
'NNS','CC','PRP','VB','VBG']
3. Lexical: counts for 30 most common unigrams in entire corpus
4. Punctuation: Counts for each punctuation mark 
5. Complexity: average number of characters per word, #unique words/#total words, number of words, Count of “long” words - words with >= 6 letters
6. Slangs: From the paper https://arxiv.org/pdf/1610.09786.pdf, it is understood that certain words like ‘WOW’, AND ‘LOL’, appear frequently in clickbait texts. By compiling the list of all the widely used and recognized slangs, the count of those slangs in the headline was considered as a feature.
7. Contractions: Words like 'they'd' or 'Here's' appeared more frequently than non-clickbait text.
8. Titlecase Words: After noticing both the set of headlines, one stark difference was noticed, that a lot of headlines of the clickbait text were titlecase texts. Meaning that the first letter of each word is capitalized. This was not seen in the texts of non-clickbait headlines. Hence, I thought it would be a good idea to include the number of ‘title-cased’ words as a feature.

## Evaluation
The feature set described above was used in 2 ways. The MultinomialNB algorithm is used in training individual features and, is leveraged in the process of combining all the features. The latter gave the best accuracy. The table below shows the accuracies on individual features:-
| Feature Set | Accuracy |
|  ----------- | ----------- |
| Stop words | 0.8736 |
| Syntax | 0.7578 |
| Lexical | 0.5 |
| Punctuation | 0.5 |
| Contractions | 0.5 |
| Slangs | 0.5 |
| Titlecase | 0.5 |
| Complexity | 0.7321 |
| All features combined | 0.9676 |
