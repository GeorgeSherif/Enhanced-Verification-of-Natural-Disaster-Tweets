![Logo](/Mohamed_bin_Zayed_University_of_Artificial_Intelligence_logo.png)

# Enhanced Verification of Natural Disaster Tweets: A Dual-Layered Approach for Improved Accuracy and Reliability
## Group 29
### Problem Statement
The rapid dissemination of information through social media, especially during natural disasters, presents a unique challenge: the need for quick verification of the authenticity and accuracy of the information being shared. This project addresses the critical issue of identifying and verifying tweets related to natural disasters. The significance of this problem lies in the potential impact of misinformation during natural disasters. False reports can lead to unnecessary panic, misallocation of resources, and even harm to those affected by the disaster. Conversely, timely and accurate information can aid in effective disaster response and management.

Our project aims to develop a system that detects tweets pertaining to natural disasters and then cross-verifies these tweets using stance classification techniques applied to articles scraped from the web. This approach intends to assess the alignment of information in tweets with that in reputable news sources, thereby evaluating their credibility. By automating this process, the system seeks to provide a rapid and reliable way of filtering and verifying information during critical times of natural disasters.

---
### Models Used
In this project, we fine-tuned the RoBERTa base and Twitter RoBERTa.

Here you can find the fine-tuned models to use directly:
[Models](https://mbzuaiac-my.sharepoint.com/:f:/g/personal/george_ibrahim_mbzuai_ac_ae/Eq84EZvljrJNgn6YDgLm-ZUBftnUf0ZkVQzZn1k_qgbdww?e=ON5s0x)

---
### Hardware Used
- A100 GPU
- T4x2
  
---
### Model Architecture
![Flowchart](https://github.com/GeorgeSherif/Enhanced-Verification-of-Natural-Disaster-Tweets/assets/65810674/e91f53e9-6e63-4296-b69e-c2ac4624a26c)
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





