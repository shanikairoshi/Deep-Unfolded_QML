# QML-and-Deep-Unfolded_QML

This repository includes the quantum machine learning implementations including 
- Deepunfolded variational quantum classifiers (DVQC), 
- Deepunfolded Quantum Neural Network (DQNN), 
- Deepunfolded Quantum Support Vector Machine (DQSVM)


Here we use qiskit based code and we introduce a novel implmentation of a deep unfolding to provide more interpretability to the optimization process for each of these qiskit algorithms. 


# System Setup - DQML with Deep Unfolding

The experiments were conducted on **Google Colab**, a cloud-based platform for running Python programs and machine learning models. This study introduced the novel concept of **Deep Unfolding** applied to both **Variational Quantum Classifier (DVQC)** and **Deep Quantum Neural Network (DQNN)**. These experiments leveraged Qiskit, an open-source SDK for quantum computing and machine learning. Below are the hardware and software configurations used in this research:

### Software Environment

- **Python version**: 3.8.15
- **Qiskit version**: 0.41.0
- **Qiskit Machine Learning version**: 0.7.2
- **Additional Dependencies**: NumPy, Matplotlib, and Scikit-learn for data handling, visualization, and preprocessing.
- 
![QML_BlockDiagram](https://github.com/user-attachments/assets/7d570a11-bd24-42de-b7fe-4267dc49ccd6)

### Quantum Neural Network (QNN)

- The QNN classifier was constructed using Qiskit's `QNNCircuit`, which consisted of:
  - **Feature map**: `ZZFeatureMap` with 2 repetitions.
  - **Ansatz**: `RealAmplitudes` with 4 repetitions.
- The model was designed for **binary classification**, with a **parity function** used to interpret quantum circuit outputs.

### Sampler Quantum Neural Network (SamplerQNN)

- A **SamplerQNN** was defined to simulate quantum circuits and compute expected values.
- The QNN was parameterized by the feature map and ansatz, with outputs interpreted using the parity function to produce binary classification labels.

### Variational Quantum Classifier (DVQC)

- A **DVQC** was implemented using Qiskit, with:
  - **Feature Map**: `ZZFeatureMap`.
  - **Ansatz**: `RealAmplitudes` for encoding the dataset into quantum circuits.

### Novel Concept: Deep Unfolding

- This study introduced the novel approach of applying **Deep Unfolding** to train both the **DVQC** and **DQNN**. Deep unfolding enabled dynamic adjustment of training parameters such as learning rate and perturbation across multiple iterations.

### Optimizer

- A custom **Simultaneous Perturbation Stochastic Approximation (SPSA)** optimizer was used with **learnable learning rate and perturbation**.
- The optimizer leveraged **meta-learning** to adjust the learning rate and perturbations dynamically. It was trained for **50 iterations**, using a **momentum factor** of 0.95 to smooth gradient calculations.

### Random Seed

- A **global random seed of 42** was set using `algorithm_globals` for reproducibility.

# Datasets

This project utilizes several well-known benchmark datasets along with a synthetic dataset provided by Qiskit for testing quantum machine learning algorithms. Below is a brief description of each dataset:

### 1. Iris Dataset
The Iris dataset consists of 150 samples of iris flowers belonging to three species: Setosa, Versicolor, and Virginica. Each sample has four features: sepal length, sepal width, petal length, and petal width. The dataset is commonly used for classification tasks.

- **Number of Samples**: 150
- **Number of Features**: 4 (sepal length, sepal width, petal length, petal width)
- **Classes**: 3 (Setosa, Versicolor, Virginica)
- **Dataset Link**: [Iris Dataset on UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/iris)

### 2. Breast Cancer Dataset (Wisconsin Diagnostic Breast Cancer - WDBC)
The Breast Cancer dataset contains 569 samples from patients with breast tumors. Each sample has 30 features that describe characteristics of the cell nuclei in images of breast masses. The dataset is used for binary classification between malignant and benign tumors.

- **Number of Samples**: 569
- **Number of Features**: 30
- **Classes**: 2 (Malignant, Benign)
- **Dataset Link**: [Breast Cancer Wisconsin (Diagnostic) Dataset on UCI](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+(Diagnostic))

### 3. Genomic Dataset
The Genomic dataset consists of gene expression data used for classifying samples based on gene activity. It is widely used in medical and biological research. This dataset presents a high-dimensional classification problem as it typically involves thousands of genes, making it suitable for applications like disease prediction (e.g., cancer).

- **Number of Samples**: Variable
- **Number of Features**: Several thousand genes (depends on the specific dataset)
- **Classes**: Variable (depends on the specific classification task)
- **Dataset Link**: [GEO (Gene Expression Omnibus) Database](https://www.ncbi.nlm.nih.gov/geo/)

### 4. Qiskit Adhoc Dataset
The Qiskit Adhoc dataset is a synthetic dataset provided by the Qiskit framework, specifically designed for testing quantum machine learning algorithms, such as Quantum Support Vector Machines (QSVM). This dataset consists of binary classification tasks, where the feature vectors are separable using quantum kernel methods. It allows for benchmarking the performance of quantum classifiers and is particularly useful for evaluating the effectiveness of quantum-enhanced feature spaces.

- **Number of Samples**: Variable (depends on the task)
- **Number of Features**: Variable (depends on the task)
- **Classes**: 2 (Binary labels: -1, 1)
- **Dataset Link**: [Qiskit Adhoc Dataset](https://qiskit.org/)



### Callback for Learning Rate and Perturbation

- A custom **deep unfolding callback** was implemented to adjust the learning rate and perturbation dynamically during optimization.
- This function used **momentum** for smoothing gradients and plotted the **objective function**, **learning rate**, and **perturbation** values after each iteration.

### Deep Unfolding Iterations

- The model was trained using **deep unfolding** over **10 iterations**.
- Key metrics such as **training accuracy**, **test accuracy**, **learning rate**, and **perturbation** were recorded at each iteration.
- **Training time** was also logged for performance evaluation.

### Results Logging

- All results were saved in a CSV file (`_training_results.csv`) for detailed analysis after each iteration.

### Conclusion

This setup provided a comprehensive and replicable environment to test the novel application of **Deep Unfolding** to **DVQC** and **DQNN** models. The use of deep unfolding in quantum machine learning presented new opportunities for dynamic optimization in t
