# QML-and-Deep-Unfolded_QML

This repository includes the quantum machine learning implementations including 
- Deepunfolded variational quantum classifiers (DVQC), 
- Deepunfolded Quantum Neural Network (DQNN), 
- Deepunfolded Quantum Support Vector Machine (DQSVM), and 
- Deepunfolded Pegasos Quantum Support Vector Classifier (DPegasosQSVC).

Here we use qiskit based code and we introduce a novel implmentation of a deep unfolding to provide more interpretability to the optimization process for each of these qiskit algorithms. 


# System Setup - DQML with Deep Unfolding

The experiments were conducted on **Google Colab**, a cloud-based platform for running Python programs and machine learning models. This study introduced the novel concept of **Deep Unfolding** applied to both **Variational Quantum Classifier (DVQC)** and **Deep Quantum Neural Network (DQNN)**. These experiments leveraged Qiskit, an open-source SDK for quantum computing and machine learning. Below are the hardware and software configurations used in this research:

### Software Environment

- **Python version**: 3.8.15
- **Qiskit version**: 0.41.0
- **Qiskit Machine Learning version**: 0.7.2
- **Additional Dependencies**: NumPy, Matplotlib, and Scikit-learn for data handling, visualization, and preprocessing.

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

### Dataset

- The **Iris dataset** from Scikit-learn was used, with features standardized for **binary classification**.
- The dataset was split into an **80/20 train-test ratio**.

### Callback for Learning Rate and Perturbation

- A custom **deep unfolding callback** was implemented to adjust the learning rate and perturbation dynamically during optimization.
- This function used **momentum** for smoothing gradients and plotted the **objective function**, **learning rate**, and **perturbation** values after each iteration.

### Deep Unfolding Iterations

- The model was trained using **deep unfolding** over **10 iterations**.
- Key metrics such as **training accuracy**, **test accuracy**, **learning rate**, and **perturbation** were recorded at each iteration.
- **Training time** was also logged for performance evaluation.

### Results Logging

- All results were saved in a CSV file (`dvqc_training_results.csv`) for detailed analysis after each iteration.

### Conclusion

This setup provided a comprehensive and replicable environment to test the novel application of **Deep Unfolding** to **DVQC** and **DQNN** models. The use of deep unfolding in quantum machine learning presented new opportunities for dynamic optimization in t
