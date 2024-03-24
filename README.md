# Credit-Card-Fraud-Detection

A binary classification model that can classify whether a credit card data is fraudulent or legit.


# Data Collection

Data has already available [here](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud). The dataset contains transactions made by credit cards in September 2013 by European cardholders. Dataset presents transactions that occurred in two days, which contains 492 frauds transactions out of 284,807 transactions. The dataset is highly imbalanced.


# Data Preprocessing

Initially datasets contains 1081 duplicate rows. After removing those it reduces to 283,726 observations, where positive (fraudulent) class contains only 0.001667% of data and negative class contains 0.998333% of data. To reduce imbalanced property, under and over sampling has done where over sampling performs well. On the other hand, under sampling perfomrs poorly.


# Model Training

Datasets is trained using `Decision Tree`, `Random Forest` and `Gradient Boosting` classification models. Showing each models performance, their training time and lackings.


# Result Analysis
In the table I showed the Precision, Recall, F1 score and  accuracy for three models.
<table>
<thead>
    <tr>
      <th>Model</th>
      <th colspan="2">Precision</th>
      <th colspan="2">Recall</th>
      <th colspan="2">F1-score</th>
      <th colspan="2">Accuracy</th>
    </tr>
    <tr>
      <th></th>
      <th>fraudulent</th>
      <th>Non-fraudulent</th>
      <th>fraudulent</th>
      <th>Non-fraudulent</th>
      <th>fraudulent</th>
      <th>Non-fraudulent</th>
      <th>fraudulent</th>
      <th>Non-fraudulent</th>
    </tr>
  </thead>
<tbody>
  <tr>
    <td>Decision Tree</td>
    <td>98.4</td>
    <td>67.03</td>
    <td>53.34</td>
    <td>53.34</td>
    <td>98.4</td>
    <td>67.03</td>
    <td>53.34</td>
    <td>53.34</td>
  </tr>
  
  <tr>
    <td>Random Forest</td>
    <td>98.4</td>
    <td>67.03</td>
    <td>53.34</td>
    <td>53.34</td>
    <td>98.4</td>
    <td>67.03</td>
    <td>53.34</td>
    <td>53.34</td>
  </tr>
  
  <tr>
    <td>Gradient Boosting</td>
    <td>98.4</td>
    <td>67.03</td>
    <td>53.34</td>
    <td>53.34</td>
    <td>98.4</td>
    <td>67.03</td>
    <td>53.34</td>
    <td>53.34</td>
  </tr>
  </tbody>
</table>

From the above table, we see that, multilabel accuracy are very closed for both the models. But, the F1 Score(Micro & Macro) of `distilroberta-base` is higher than `distilbert-base-uncased` model's F1 Score. So, we can say that, `distilroberta-base` performed slightly better for the given dataset.

# Model Compression and ONNX Inference
The trained model has a memory of 300+ MB. I compressed this model using ONNX quantization and brought it to ~78.8 MB.

# Model Deployment

The compressed model is deployed to HuggingFace Spaces Gradio App. The implementation can be found in `deployment` folder or see live [here.](https://huggingface.co/spaces/MdTanvirHossain/QA_Classifier)

<img src="deployment/gradio_app_2.PNG" alt="Girl in a jacket" style="width:1600px;height:400px;"> </br>


# Web Deployment
Deployed a Flask App built to take question description and show the categories as output. Check `flask` branch for the details. The website is live [here.](https://multilabel-question-category-classifier.onrender.com)
</br></br>
<img src="deployment/flask_app_home.PNG" alt="Girl in a jacket" style="width:1000px;height:500px;"></br></br>
<img src="deployment/flask_app_result.PNG" alt="Girl in a jacket" style="width:1000px;height:500px;">
