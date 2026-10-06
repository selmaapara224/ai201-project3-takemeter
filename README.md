🎯 Baseline accuracy: 0.810  (evaluated on 21/21 parseable responses)

Per-class metrics (baseline):
              precision    recall  f1-score   support

  oldhead       0.89      0.73      0.80        11
  youngin       0.75      0.90      0.82        10

  accuracy                           0.81        21
   macro avg       0.82      0.81      0.81        21
weighted avg       0.82      0.81      0.81        21


🎯 Fine-tuned model accuracy: 0.524

Per-class metrics (fine-tuned model):
              precision    recall  f1-score   support

  oldhead       0.52      1.00      0.69        11
  youngin       0.00      0.00      0.00        10

  accuracy                           0.52        21
   macro avg       0.26      0.50      0.34        21
weighted avg       0.27      0.52      0.36        21


Confusion Matrix after run in new session

<img width="509" height="490" alt="Confusion Matrix 2 Project 3" src="https://github.com/user-attachments/assets/427d9478-3b79-44f7-823c-c416e444780d" />


Sample Classifications:

| Post (truncated) | True label | Predicted | Confidence | Correct? |
|---|---|---|---|---|
| What are you doing? | oldhead | oldhead | 0.54 | yes |
| Do you see the mountains? | oldhead | oldhead | 0.54 | yes |
| It’s blurry. Try to send it to my email. | oldhead | oldhead | 0.52 | yes |
| I still dunno my schedule frfr | youngin | oldhead | 0.54 | no |
| i like dat | youngin | oldhead | 0.53 | no |

Paste this table into your README under 'Sample Classifications'.
For at least one correct row, add a sentence on why that prediction is reasonable.

Wrong predictions: 10 / 21

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

Analysis:
I genuinely have no clue as to why this happened, because the predictions were near perfect on the first run. I did not save all of the information the first time, but have the confusion matrix below. The first matrix is from the most recent run, and the second one is from the first run I did. I had to restart the session due to inactivity, but don't know why the results skewed this way, especially after the baseline was so good.


Confusion Matrix after FIRST run
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


