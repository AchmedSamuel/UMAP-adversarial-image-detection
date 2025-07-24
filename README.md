# UMAP-adversarial-image-detection
A repository of jupyter notebooks on the paper **"Uniform Manifold Approximation and Projection and eXplainable Artificial Intelligence to Detect Adversarial Machine Learning"** on the MNIST and CIFAR datasets authored by Koroma A.S., Narteni S., Cambiaso E., & Mongelli M.
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


