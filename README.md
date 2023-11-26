# Enhanced Verification of Natural Disaster Tweets: A Dual-Layered Approach for Improved Accuracy and Reliability
The rapid dissemination of information through social media, especially during natural disasters, presents a unique challenge: the need for quick verification of the authenticity and accuracy of the information being shared. This project addresses the critical issue of identifying and verifying tweets related to natural disasters. The significance of this problem lies in the potential impact of misinformation during natural disasters. False reports can lead to unnecessary panic, misallocation of resources, and even harm to those affected by the disaster. Conversely, timely and accurate information can aid in effective disaster response and management.

Our project aims to develop a system that detects tweets pertaining to natural disasters and then cross-verifies these tweets using stance classification techniques applied to articles scraped from the web. This approach intends to assess the alignment of information in tweets with that in reputable news sources, thereby evaluating their credibility. By automating this process, the system seeks to provide a rapid and reliable way of filtering and verifying information during critical times of natural disasters.

---
### Models Used
In this project, we fine-tuned the RoBERTa base and Twitter RoBERTa.

Here you can find the fine-tuned models to use directly:
[Models](https://mbzuaiac-my.sharepoint.com/:f:/g/personal/george_ibrahim_mbzuai_ac_ae/Eq84EZvljrJNgn6YDgLm-ZUBftnUf0ZkVQzZn1k_qgbdww?e=ON5s0x)

---
### Using the models
```python
best_model = SentimentClassifier()
best_model.load_state_dict(torch.load('best_model_state.bin'))
```

```python
model_path = "/RoBERTa_Fever_7(Balanced)"
#model_path = "/RoBERTa_Fever_6" #Unbalanced
tokenizer = RobertaTokenizer.from_pretrained(model_path)
model = RobertaForSequenceClassification.from_pretrained(model_path)
```
---
### Hardware and Packages Used
All packages used in our conda environment are included in the Requirements.txt  

- A100 GPU
- T4x2

---
### Datasets Used
We used 2 datasets for this project.

1- Natural Language Processing with Disaster Tweets - [Kaggle](https://www.kaggle.com/competitions/nlp-getting-started)
 
 Features:
  - ID
  - Keyword
  - Location
  - Text
 
  Output:
  - 0: Not Natural Disaster
  - 1: Natural Disaster
  
  The distribution of data can be shown in the following table

  | Output | Count 2 | % |
  | :---            | ---:            | ---: |
  | 0  | 4,342   | 57% |
  | 1  | 3,271   | 43% |

2- Fact Extraction and VERification - [FEVER](https://huggingface.co/datasets/mwong/fever-evidence-related/viewer/default/train) 
  
  Features:
  - ID
  - Claim
  - Evidence
  - input_ids
  - attention_mask
  
   Output:
   - 0: Evidence does not support the claim
   - 1: Evidence supports the claim

  
  The original training dataset imported from the datasets hugging face library includes
  
  | Output | Count 2 | % |
  | :---            | ---:            | ---: |
  | 0  | 284,502   | 70.6% |
  | 1  | 118,716   | 29.4% |



---
### Model Architecture
![Flowchart](https://github.com/GeorgeSherif/Enhanced-Verification-of-Natural-Disaster-Tweets/assets/65810674/e3244049-56c4-48f9-a2e4-e6c7b030119e)

---
Every tweet is initially processed by the first layer of our model, where it is classified to determine if it relates to a natural disaster. Following this, the tweet, along with a document retrieved from the Google Search Custom Search API, is passed to the second layer. This layer carries out stance classification, assessing whether the information in the tweet is corroborated by the document or not.

---
### Evaluation
We used the accuracy, precision, recall, and f1-score metrics from scikit-learn.
Results showed the following for the first layer:
- Accuracy: 82.81%
- Precision: 81.61%
- Recall: 77.37%
- F1 Score: 79.43%

For the second layer, evaluation was carried out in 3 phases. They can be listed as follows:
- Second layer output compared to the true labels.
![image](https://github.com/GeorgeSherif/Enhanced-Verification-of-Natural-Disaster-Tweets/assets/65810674/1ec9fe40-0f90-47d7-98ad-ec86eefa134a)
- Second layer output compared to the true labels when the first layer correctly classified the tweet.
![image](https://github.com/GeorgeSherif/Enhanced-Verification-of-Natural-Disaster-Tweets/assets/65810674/01d70120-da51-4261-9c21-12ed8af5591e)
- Second layer output compared to the true labels when the first layer incorrectly classified the tweet.
![image](https://github.com/GeorgeSherif/Enhanced-Verification-of-Natural-Disaster-Tweets/assets/65810674/f63c0344-28c4-4b5c-b950-935f5a027306)

--- 
### Conclusion
The rise of social media has amplified the challenge of fake news, prompting us to develop a two-tiered system for verifying tweets about natural disasters. Our model, which combines BerTopic for feature extraction and RoBERTa for classification, surpassed the baseline with a 4.9% higher F1 score of 0.82653. In stance classification, it achieved 77% agreement on correctly classified tweets from the first layer and notably corrected 76% of the misclassifications made by the first layer, demonstrating its effectiveness in tackling misinformation.

---
### Team Members
- Hanin Atwany
- George Ibrahim
- Ching Chao



