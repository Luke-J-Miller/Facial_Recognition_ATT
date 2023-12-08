# Face Recognition Using Deep Learning: A Study on the Georgia Tech Dataset
### Presented by Luke Miller as the Final Project for CS5567

## Project Overview
In this project, I explored face recognition using InceptionV3, a pre-trained CNN, applied to the Georgia Tech face recognition dataset. The focus was on employing transfer learning for accurate subject identification. Four distinct models were compared: subject-independent, subject-dependent with and without dropout, and with regularization. PCA was also applied to the subject-dependent model for dimensionality reduction [1].

## Methodology Overview
Transfer learning was employed using the InceptionV3 model, tailored to the Georgia Tech face dataset. The architecture was adapted for face recognition, focusing on maximizing identification accuracy across different subjects.

## Data Preparation
The Georgia Tech dataset comprises images from 50 subjects, each with 15 instances. The first 10 images per subject were used for training/validation, while the last 5 were for testing. Image preprocessing included normalization, alignment, resizing, and augmentation to enhance model robustness [2]. Horizontal flips were not used because it significantly decreases the recognizability of faces.  

  ![image](https://github.com/Luke-J-Miller/Facial_Recognition_ATT/assets/111100132/a6ecf8aa-a1e1-453e-a5c0-bb33d0f3ee53)  

## Network Architecture
The InceptionV3 architecture was selected for its efficiency in image recognition tasks. The classification head of the network was redesigned with a global average pooling layer, followed by dense layers. The model underwent a four-stage fine-tuning process, with progressive layer unfreezing and learning rate adjustments [3].

## Feature Extraction and Biometric Templates
Features, serving as biometric templates, were extracted from the layer prior to the classification head. These features capture the unique facial characteristics of each individual and were used for evaluating the abilities of the model[3].


##  Score Distribution and ROC Curve
I calculated cosine distance similarity[4] between biometric templates, generating scores for both genuine (same subject) and impostor (different subjects) pairings. The ROC curve demonstrates the model's discriminative power, with a true positive rate plotted against the false positive rate. The subject-dependent model achieved an ROC AUC of 0.97, signifying high accuracy, and a d-prime value of 2.66, indicating strong separability between genuine and impostor scores.

![image](https://github.com/Luke-J-Miller/Facial_Recognition_ATT/assets/111100132/ac1a0eed-c991-445b-9349-a824b37900c6)  



## PCA Dimensionality Reduction
PCA reduced feature dimensions while preserving 95% of the variance. This enhanced model efficiency with minimal performance loss. The PCA-applied model showed an AUC of 0.97 and a d-prime of 2.72.  
  
![image](https://github.com/Luke-J-Miller/Facial_Recognition_ATT/assets/111100132/ddf41b0f-62c5-4cc3-bccf-ee976b527da8)  

  
## Rank 1 and Rank 5 Identification Rates
The model exhibited a perfect rank 1 identification rate of 1.0. With such high accuracy, the rank 5 rate was also naturally 1.0. Post-thresholding, these rates remained unchanged, underscoring the model's robustness.

## Subject-Independent Protocol
In the subject-independent protocol, a new model was trained using the same parameters as before, but it was only trained on 40 of the 50 subjects.  The remaining 10 subjects were used for testing its performance on classifying faces not seen in training based upon the cosine distance of features from a genuine set based upon an enrollment picture, and an impostor set consisting of all-other subjects. The model only slightly underperformed the subject dependent model with a ROC AUC of 0.96, and a d' of 2.56.
  
![image](https://github.com/Luke-J-Miller/Facial_Recognition_ATT/assets/111100132/a0a9a645-91e9-479e-a1d2-d559302d9889)  
  

## Committee of Models
A committee of three models, each with variations in dropout, regularization, and pooling, was formed. This approach aimed at capturing diverse learning patterns for improved prediction[5]. By averaging the outputs of these models, the combined predictions achieved a remarkable ROC AUC of 1.00 and a d-prime of 3.71, demonstrating the efficacy of ensemble techniques. The ensemble model significantly outperformed its individual counterparts, highlighting the advantages of combining diverse learning models in deep learning applications.
  
![image](https://github.com/Luke-J-Miller/Facial_Recognition_ATT/assets/111100132/c2c5544d-0d59-4234-b906-be8ce3cdebdf)  
   

## Conclusion
This project underscores the effectiveness of transfer learning in facial recognition and the benefits of PCA for efficiency. It also demonstrates the enhanced predictive power achievable through ensemble methods.  

## References
[1] I. Goodfellow, et al. Deep Learning. Cambridge: MIT Press, 2016, pp 147
[2] I. Goodfellow, et al. Deep Learning. Cambridge: MIT Press, 2016, pp 240
[3] I. Goodfellow, et al. Deep Learning. Cambridge: MIT Press, 2016, pp 321
[4] I. Goodfellow, et al. Deep Learning. Cambridge: MIT Press, 2016, pp 269
[5] I. Goodfellow, et al. Deep Learning. Cambridge: MIT Press, 2016, pp 250


