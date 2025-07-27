# UMAP-adversarial-image-detection
A repository of jupyter notebooks on the paper **"Uniform Manifold Approximation and Projection and eXplainable Artificial Intelligence to Detect Adversarial Machine Learning"** on the MNIST and CIFAR datasets authored by Koroma A.S., Narteni S., Cambiaso E., & Mongelli M.

In order to promote reproducibility and transparency in adversarial ML research, standard image datasets that are openly available such as MNIST handwritten digits (http://yann.lecun.com/exdb/mnist/) and CIFAR  (https://www.cs.toronto.edu/~kriz/cifar.html) datasets are utilized. These datasets used in this experiment enable rapid prototyping of attacks and detectability, providing clear comparison for adversarial robustness. The adversarial tool used during the experiments is the adversarial robustness toolbox and UMAP as a compression tool. They are all open-source tools that are widely used in various machine learning experiments. CNN models are built from scratch with accuracies above 99.0% and 74% for MNIST and CIFAR datasets respectively 
Our complete implementation uses Python open-source ecosystems including TensorFlow and other necessary libraries. The repository includes: 

• CNN scripts of MNIST & CIFAR10 datasets and pretrained CNN model weights.

• Scripts for attack methods such as CW, FGSM and DeepFool. 

• Jupyter notebooks demonstrating the embeddings of both legitimate and malicious datasets of UMAP experiments.

• Generated adversarial UMAP datasets.

• Detection scripts.

The dataset of both legitimate and malicious are separately embedded via UMAP and later vertically combined to generate a single csv file detailing the features, umap1, umap2 and attack for 2D. Each dataset, legitimate and malicious, has 10,000 rows with the first 10,000 rows representing legitimate where attack column is ‘0’ and from 10,001 row to the 20,000 row are malicious with ‘1’ representing attack. The same structure is followed for different dimensions (3D, 5D, 10D) with a variability in the number of features as the number of dimensions increases while the attack column remains constant. The dataset generated 2D, 3D, 5D and 10D for the Carlini-Wagner, FGSM and DeepFool attacks can be found in the dataset folder. 



Attacking techniques like fast sign gradient methods, Carlini-Wagner and DeepFool are investigated by the embeddings of both legitimate and malicious MNIST and CIFAR-10 dataset via UMAP for various dimensionality reduction. 


# Code usage
To generate UMAP data for FGSM, Carlini and DeepFool attacks, install the adversarial robustness toolbox, UMAP and import all required libraries as in the jupyter notebooks.  

Code Structure: We organize the code structure into two main phases:
1. Before Detection: Attack Generation (**generate_UMAP_adversarial_fgsm_CW.ipynb / generate_adversarial_DeepFool.ipynb**)
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

- Use the saved CSV files for 2D and 3D to visualize the decision boundary between legitimate and adversarial images. script name (e.g. **fgsm_cw_DeepFool_UMAP_2D_3D_viz.ipynb**) 

2. After UMAP: Attack Detection (script name: (**UMAP_detection_metrics_ f eat_rules_cv..ipynb**)
    i. Load UMAP (2D, 3D, 5D, 10D.) csv files
    ii. Train DT classifier on loaded UMAP (2D, 3D, 5D, 10D.) csv files.
    iii. Compute comfusion matrix and metrics (TPR, TNR, FPR, FNR,...)
    iv. Extract importance feature rangings.
    v. Generate if-then rules.


