***Course Name***
深度學習實作與應用

***Course Number***
IM5062

***Group Members***
R12725037 蘇勁安
R12725018 汪佩璇
R12725040 許方怡
R12725073 楊郁姸

---
## Project Info

此專案透過實作深度學習模型來協助判別文章是否由 AI 生成，以此加強論壇的透明度、提升論壇的可信度，以及促進商家間的公平競爭。

### Data Source
1. PTT 撰寫的食記 1007 篇：訓練、測試
2. ChatGPT 生成文章 1006 篇：訓練、測試
3. Breeze 模型生成文章 1007 篇：額外測試

## Usage
With Python 3.10 installed, run

```shell
    $ pip install -r requirements.txt
```

to install all required package.

## File Intro

1. Classifier
- GRU_10Fold.ipynb
- GRU_NewData_Classifier.ipynb
- KNN_10_10Fold.ipynb
- KNN_NewData_Classifier.ipynb
- LogisticRegression_10Fold.ipynb
- LogisticRegression_NewData_Classifier.ipynb
- MLP_10Fold.ipynb: 對現有資料做訓練
- MLP_NewData_Classifier.ipynb: 對 Breeze 資料做測試
- random_forest_10Fold.ipynb
- random_forest_NewData_Classifier.ipynb
- svm_forest_10Fold.ipynb
- svm_NewData_Classifier.ipynb
- XGBoost_10Fold.ipynb
- XGBoost_NewData_Classifier.ipynb

2. TextVectorize
- BertModel.ipynb: 透過現有資料訓練BERT Model，使用BERT提供的 tokenlizer 對資料 token 化後輸入 BERT 架構訓練模型
- Ollama_API.ipynb: 透過 local LLM 建置，access Breeze:7b (聯發創新基地（MediaTek Research）開源的MediaTek Research Breeze-7B模型 (以下簡稱 MR Breeze-7B)，憑藉其參數量少且性能卓越的特點，期望能對學術界和產業界在人工智能領域的進一步發展帶來正面影響。)
- PTTCrawler.ipynb: PTT 爬蟲程式
- TextToVec_BERT_self_train.ipynb: 將所有資料透過自訓練 BERT 模型轉成 vector
- TextToVec_Combine.ipynb: 將所有資料透過 tfidf, word2vec, BERT (Google Trained) 轉成 vector
- TextToVec_GPT.ipynb: 測試 GPT 資料轉 vector
- TextToVec_Ollama.ipynb: 將 Breeze 資料轉 vector
- TextToVec_Word2vec_self_train.ipynb: 將所有過自訓練 word2vec 模型轉成 vector
- word_embeddings.npy: 自訓練 word2vec 模型
- Word2vecModel.ipynb: 透過現有資料訓練 Word2vec Model

## Results
1. F2-Score Comparison

| Model                  | Logistic Classifier | Random Forest | SVM   | XGBoost | KNN   | MLP   | GRU   |
|------------------------|---------------------|---------------|-------|---------|-------|-------|-------|
| **TF-IDF**             | 0.9961              | 1.0000        | 0.9922| 1.0000  | 0.9702| 0.9865| 0.9922|
| **Word2Vec**           | 0.9932              | 0.9580        | 0.9815| 0.9737  | 0.9807| 0.9883| 0.9844|
| **Word2Vec (self-train)** | 0.9834          | 0.9834        | 0.9942| 0.9893  | 0.9766| 0.9961| 0.9951|
| **BERT**               | 0.9961              | 1.0000        | 0.9961| 0.9951  | 0.9646| 0.9961| 1.0000|
| **BERT (self-train)**  | 0.9961              | 0.9949        | 0.9961| 0.9951  | 0.9646| 1.0000| 1.0000|

2. Breeze Data Accuracy Comparison

| Model                  | Logistic Classifier | Random Forest | SVM   | XGBoost | KNN   | MLP   | GRU   |
|------------------------|---------------------|---------------|-------|---------|-------|-------|-------|
| **TF-IDF**             | 0.9633              | 0.9384        | 0.9851| 0.9633  | 0.8769| 0.6802| 0.9772|
| **Word2Vec**           | 0.7587              | 0.7021        | 0.7825| 0.6862  | 0.5909| 0.7627| 0.7239|
| **Word2Vec (self-train)** | 0.7031          | 0.6435        | 0.7577| 0.6475  | 0.7200| 0.7676| 0.6931|
| **BERT**               | 0.8957              | 0.8510        | 0.8878| 0.8133  | 0.8918| 0.8342| 0.8272|
| **BERT (self-train)**  | 0.0010              | 0.9871        | 0.0000| 0.0000  | 0.0149| 0.9990| 0.9990|

## Note
模型因檔案較大，不放入 Github 中