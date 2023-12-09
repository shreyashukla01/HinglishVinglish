# HinglishVinglish
NLP solution for Hindi &amp; English code-mixed classification problem

`domain_adaptation.ipynb` includes:
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
