# UMAP-adversarial-image-detection
A repository of jupyter notebooks on the paper **"Explainable AI for detection of adversarial machine learning via UMAP and open data"** on the MNIST and CIFAR datasets authored by Koroma A.S., Narteni S., Cambiaso E., & Mongelli M.
Attacking techniques like fast sign gradient methods, Carlini-Wagner and DeepFool are investigated by the embeddings of both legitimate and malicious MNIST and CIFAR dataset via UMAP for various dimensionality reduction. 


# Code usage
To generate UMAP data for FGSM, Carlini and DeepFool attacks, install the adversarial robustness toolbox, UMAP and import all required libraries as in the jupyter notebooks.  
Load the trained CNN model. Generate the legitimate dataset via UMAP for 2D, 3D, 5D and 10D. Impliment the attack (FGSM/Carlini) to generate the malicious datasets for 2D, 3D, 5D and 10D. Then concatenate the generated ligitimate and and malicious datasets in a single .csv file.


Code Structure: We organize the project into two phases:
1. Before Detection: Attack Generation
  i. Load MNIST/CIAFR10 datasets.
  ii. Generate reduced transform UMAP 2D, 3D, 5D and 10D using test set (MNIST/CIFAR10) for both legitimate and addversarial samples.
  iii. Load pretrained CNN models (mnist_CNN_model.h5/cifar10_CNN_model.h5).
  iv. Wrap the loaded CNN model with the Keras classifier.
  v. Generate adversarial samples using FGSM/Carlini/DeepFool.
  vi. Measure attack success rate (i.e., misclassified examples).
  vi. Transform the generated FGSM/Carlini/DeepFool adversarial test set to UMAP 2D, 3D, 5D and 10D.
  vii. Labeled samples as attack = 1 for adversarial, 0 for legitimate.
  viii. Combine legitimate and adversarial UMAP data 
  xi. Output legitimate and adversarial UMAP data and saved as CSV files.

2. After UMAP: Attack Detection
- Load UMAP (2D, 3D, 5D, 10D.) csv files
- Train DT classifier on loaded UMAP (2D, 3D, 5D, 10D.) csv files.
- reduced data to compute metrics
- Generate if-then DT rules
- Visualize the decision boundary between clean and adversarial images
- Importance feature extraction
