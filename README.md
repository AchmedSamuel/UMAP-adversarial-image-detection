# UMAP-adversarial-image-detection
A repository of jupyter notebooks on the paper **"Explainable AI for detection of adversarial machine learning via UMAP and open data"** on the MNIST and CIFAR datasets authored by Koroma A.S., Narteni S., Cambiaso E., & Mongelli M.
Attacking techniques like fast sign gradient methods, Carlini-Wagner and DeepFool are investigated by the embeddings of both legitimate and malicious MNIST and CIFAR dataset via UMAP for various dimensionality reduction. 


# Code usage
To generate UMAP data for FGSM, Carlini and DeepFool attacks, install the adversarial robustness toolbox, UMAP and import all required libraries as in the jupyter notebooks. 
Load the trained CNN model. Generate the legitimate dataset via UMAP for 2D, 3D, 5D and 10D. Impliment the attack (FGSM/Carlini) to generate the malicious datasets for 2D, 3D, 5D and 10D. Then concatenate the generated ligitimate and and malicious datasets in a single .csv file.


code Structure: We organize the project into two phases:
Before Detection: Attack Generation
- Generate adversarial examples (FGSM, DeepFool, Carlini-Wagner)
- Measure attack success rates
- Output: Clean and adversarial UMAP data

After UMAP: Detection Phase
- Apply UMAP (2D, 3D, 5D, 10D.)
- Train DT classifier on reduced data to compute metrics
- Generate if-then DT rules
- Visualize the decision boundary between clean and adversarial images
- Importance feature extraction
