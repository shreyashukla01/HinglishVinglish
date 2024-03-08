# HinglishVinglish 
**NLP solution for Hindi & English code-mixed classification**

This project is an academic project created for the course INF385T : Natural Language Processing and Applications

Team KNS (Shreya Shukla - https://github.com/shreyashukla01, Krishna Sri Somepalli - https://github.com/krishnasriSomepalli)

### Motivation
The objective of this project is to design an aggression detection system that can detect offensive comments from Social Media websites. Though there are prevalent systems that do that for comments in English, there is only some development in the Hindi English code mixed data where Hindi and English words exist together and can use script of both languages.

We used **classic Machine Learning models** and **multilingual deep learning models like mBERT** to perform a comprehensive analysis.

### Dataset 
The TRAC dataset (https://sites.google.com/view/trac1/shared-task) is primarily utilized in this project. This subset includes an aggression tagset and an annotated corpus of Hindi-English code-mixed data, derived from social media platforms, including Facebook and Twitter.

The corpus is annotated with three distinct tags: CAG (Covertly Aggressive), OAG (Overtly Aggressive), and NAG (Non-Aggressive)

<img width="505" alt="Screenshot 2024-02-19 at 5 23 55 PM" src="https://github.com/shreyashukla01/HinglishVinglish/assets/30028998/254181bb-c1f2-4f5c-bdb8-4b8db6616df0">

### Data Cleaning
Our data cleaning approach entails: 

- **Identification of Language Components:** For Hindi-English code-mixed data, we adopt a strategy that retains essential elements like "matra" or "diacritic marks" and sentence-concluding symbols like ‘।’ for accurate tokenization. 

- **Removal of Noise and Irrelevant Characters:** We eliminate URLs, mentions, hashtags, smileys, emoticons, digits, and certain symbols like ‘-’, ‘(‘, ‘)’, ‘\n’. Important punctuation marks such as ‘.’, ‘?’, or ‘।’ are retained, while multiple occurrences of characters are replaced with a single instance, ensuring a cleaner dataset for analysis.


### Ablation Study
We Conducted an **ablation study** on translated data using machine learning models like SVM, MLP Classifier, and Logistic Classifier on different language features like Bag-of-words, Glove, Bigrams and Tf-idf features.

Preprocessing for ablation study (Translation using Google API) -

It was essential to use individual sentences for translation with Google API. We followed the following approach to get the translated data.

**Before split operation** -
मोहन हँसकर बोला, how are you? dikhe nahi kitne dinon se.

**After split operation** -
[‘मोहन हँसकर बोला’, ‘how are you’, ‘dikhe nahi kitne dinon se’]

**Translate each sentence separately and join** -
[mohan said laughingly how are you haven't seen you for so many days]

The **MLP Classifier** consistently demonstrates superior performance across both the combined and individual datasets when compared to the other two classifiers (54.39%)

### Multilingual models

Using TRAC extended datasets, the performance of the **mBERT language mode**l was enhanced through **masked language model (MLM) fine-tuning**.

Following are the metrics for comparison of trained mBERT model performance **between plain and transliterated data** to assess effectiveness.

1. `bert-base-multilingual-cased` fine-tuned with TRAC-extended dataset. Accuracy: 54%
2. `bert-base-multilingual-uncased` fine-tuned with MLM objective on Hinglish-TOP dataset. Perplexity: 246.65 -> 6.93  
  i. Finetuned with TRAC-extended dataset. Accuracy: 50%  
  ii. Transliterating TRAC-extended dataset using indic-trans -> TRAC-extended-transliterated  
  iii. Finetuned with TRAC-extended-transliterated dataset. Accuracy: 0.49%  
3. `bert-base-multilingual-uncased` fine-tuned with MLM objective on TRAC-extended-transliterated dataset. Perplexity: 47.93 -> 38.25 for TRAC-extended and 129.54 -> 99.48 for TRAC-extended-transliterated  
  i. Finetuned with TRAC-extended dataset. Accuracy: 52%  
  iii. Finetuned with TRAC-extended-transliterated dataset. Accuracy: 52%  
4. `bert-base-multilingual-uncased` fine-tuned with MLM objective on TRAC-extended dataset. Perplexity: 47.93 -> 39.48 for TRAC-extended and 129.54 -> 89.50 for TRAC-extended-transliterated  
  i. Finetuned with TRAC-extended dataset. Accuracy: 52%  
  iii. Finetuned with TRAC-extended-transliterated dataset. Accuracy: 51%
