## Takemeter

**Community:** I chose my friends, family, and extended community as the community. This is a good fit for the classification task because there is a nuanced but still obvious difference in the way different types of people communicate with me via text.

**Labels:**

OldHead: A text from an older person. My mom, aunts and uncles, teachers, older mentors etc. You can normally tell by the grammar they use, what type of (if any) emojis, and the subject matter.

  Example 1: Hi Selma, thank you my precious niece. 🤗😘♥️
  Example 2: Yes, it is. You can delete it from your phone
  
Youngin: A text from one of my peers. My friends, close-in age cousins, classmates, etc. You can tell by the grammar they use as well, how many abbreviations are in the text, the subject matter, and in what context different emojis are used.
 
  Example 1: i like dat
  Example 2: u right

**Data collection:**

I will collect data from my own text messages. There is a possibility for there to be more texts from the Youngin category, since younger people tend to communicate via text more than older people. 

## Results

**🎯 Baseline accuracy:** 0.810  (evaluated on 21/21 parseable responses)

Per-class metrics (baseline):
              precision    recall  f1-score   support

  oldhead       0.89      0.73      0.80        11
  youngin       0.75      0.90      0.82        10

  accuracy                           0.81        21
   macro avg       0.82      0.81      0.81        21
weighted avg       0.82      0.81      0.81        21


**🎯 Fine-tuned model accuracy:** 0.524

Per-class metrics (fine-tuned model):
              precision    recall  f1-score   support

  oldhead       0.52      1.00      0.69        11
  youngin       0.00      0.00      0.00        10

  accuracy                           0.52        21
   macro avg       0.26      0.50      0.34        21
weighted avg       0.27      0.52      0.36        21


**Confusion Matrix after run in new session:** 

<img width="509" height="490" alt="Confusion Matrix 2 Project 3" src="https://github.com/user-attachments/assets/427d9478-3b79-44f7-823c-c416e444780d" />


**Sample Classifications:**

| Post (truncated) | True label | Predicted | Confidence | Correct? |
|---|---|---|---|---|
| What are you doing? | oldhead | oldhead | 0.54 | yes| **This classification is reasonable because it follows perfect grammar and punctuation, a marker of "oldhead" texts.**
| Do you see the mountains? | oldhead | oldhead | 0.54 | yes |
| It’s blurry. Try to send it to my email. | oldhead | oldhead | 0.52 | yes |
| I still dunno my schedule frfr | youngin | oldhead | 0.54 | no |
| i like dat | youngin | oldhead | 0.53 | no |



**Wrong predictions: 10 / 21**

--- #1 ---
Text:      I still dunno my schedule frfr
True:      youngin
Predicted: oldhead  (confidence: 0.54)

--- #2 ---
Text:      i like dat
True:      youngin
Predicted: oldhead  (confidence: 0.53)

--- #3 ---
Text:      730 ish🫩
True:      youngin
Predicted: oldhead  (confidence: 0.52)

**Analysis:**

The predictions were near perfect on the first run. I had to restart the session due to inactivity, and did not save all of the information the first time, but have the confusion matrix below. The first matrix is from the most recent run, and the second one is from the first run I did.  It is very surprising that the second run had such skewed results, but after asking Claude, the issue appears to be that the fine tuning data had one more message labeled as "oldhead", so the model overfit to the majority. What would likely fix this skewing is more data.


**Confusion Matrix after FIRST run:**
<img width="509" height="490" alt="Confusion Matrix Project 3" src="https://github.com/user-attachments/assets/ca32ee7b-bbf0-4b62-8980-2304dc2515a7" />


==================================================
RESULTS COMPARISON
==================================================
Model                               Accuracy
---------------------------------------------
Zero-shot baseline (Groq)              0.810
Fine-tuned DistilBERT                  0.524
---------------------------------------------

Fine-tuning regression: 0.286


## AI Usage:

I used Claude to understand what the different evaluation metrics were, and to get deeper understanding on machine learning.
I also used it to analyze why my two runs differed so much. When I gave Claude my two drastically different confusion matrices, told it that they were from two different session, and asked why this happened, it asked me what type of model was being used. I told it that DistilBERT was used and this was it's response:

  That narrows it down: DistilBERT fine-tuning on a dataset this small is known to be unstable, and the all-oldhead matrix is a classic symptom.

  Why DistilBERT is especially prone to this

  The classification head starts random. DistilBERT's body is pretrained, but the small layer that outputs oldhead/youngin is initialized from     scratch each run. Different seeds give different starting points, and with only a few dozen training examples there aren't many gradient steps   to recover from a bad one.
  Collapse to one class is common with tiny data. If the learning rate is a bit high, or there are too few steps, the model can settle on       "always predict the majority class" because that's the cheapest way to reduce loss early on. Your 11 vs 10 split fits this: it picked the   slightly larger class.
  Small test sets amplify it. On 21 examples you can't tell a mediocre model from a lucky one.
  Restarting the session resets everything. Seeds, the random head initialization, and possibly the train/test split all change unless you fixed   them explicitly. If the split is random and unseeded, the second run may also have trained on a different set of texts.


