**REPORT**

I have split given dataset into train and test set with separation 80%-20% respectively, using random seed=1234 when shuffling the dataset. I have used both titles and abstracts as separate inputs to the all deep neural network I have tried. I have changed categorical labels to binary integers. '0' for Chemistry and '1' for Material Science.

For this project, I have tried three different approaches:
1) One of them is to create word embeddings from scratch, using Tensorflow Tokenizer and Keras Embedding Layer. This approach has given the validation accuracy around 0.67. 

2) I have tried to use pre-trained word embeddings of Tensorflow, which are trained using Google News and has 50-dimensional embeddings for each word. Then, it combines them to have sentence embedding. The specific details can be found at this [url](https://tfhub.dev/google/nnlm-en-dim50-with-normalization/2). I have embedded titles and abstracts separately. Then merged them into a vector and feed them into two dense layers and a final layer with activation sigmoid. I have used dropout layers and L2 regularisation to overcome the overfitting problem. This approach resulted in 0.72 validation accuracy. I have also done experiments with 128-dimensional embeddings of same architecture, it gave slightly better results than 50-d case. However, model weights file became very large. 

3) Lastly, I have tried pre-trained BERT architecture, but it resulted poorly (around 0.50 validation accuracy).

So, I have decided to go on with my 2nd approach. Accuracy, F-1 score, AUC score and confusion matrix can be found below. 

Note: Although, I have used 50-dimensional embeddings, model weight files are still huge (~1 GB). Therefore, I could not include them into my GitHub repository. You can access and download the models directory using the link below. I have also added this link to GitHub issues.
[Models folder](https://drive.google.com/drive/folders/1-vrzQdjcqbEr5CLW8u9E2fPAukZen4qH?usp=sharing)



**METRICS**

**Test set accuracy:** 0.695

**Area Under the ROC Curve:** 0.767
(ROC and Precision Recall Curves are added to GitHub repository.)

                  precision    recall  f1-score   support

    Material Science   0.73      0.62      0.67       752
       Chemistry       0.67      0.77      0.72       747

        accuracy                           0.70      1499
       macro avg       0.70      0.70      0.69      1499
    weighted avg       0.70      0.70      0.69      1499

**Confusion Matrix:**

    [[466 286]
    [171 576]]

