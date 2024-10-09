# QML-and-Deep-Unfolded_QML

This repository includes the quantum machine learning implementations including 
- variational quantum classifiers (VQC), 
- Quantum Neural Network (QNN), 
- Quantum Support Vector Machine (QSVM), and 
- Pegasos Quantum Support Vector Classifier (PegasosQSVC).

Here we use qiskit based code and we introduce a novel implmentation of a deep unfolding to provide more interpretability to the optimization process for each of these qiskit algorithms. 


# System Setup
Google Colab is a cloud-based platform for running Python programs and machine learning models, where the experiments were conducted. This study used the Qiskit,an open source sdk for quantum computing Machine Learning Framework. Configurations for hardware and software used in this article are as follows:

- Python software environment: Python 3.8.15, qiskit 0.41.0 and qiskit-ml 0.7.2 were used for the computations in this study It also required a few more dependencies such as Numpy, Matplotlib and Scikit-learn (to use the dataset)

- Applying Quantum algorithms: Implemented a Variational Quantum Classifier (VQC) using Qiskit. Feature map was ZZFeatureMap and for ansatz the RealAmplitudes were used to encode dataset into quantum circuit.

- Optimiser: We created a custom Simultaneous Perturbation Stochastic Approximation (SPSA) for training the model with learnable learning rate and perturbation. The optimizer leveraged meta-learning to tune the learning rate schedule and perturbations. The optimizer was trained with 50 iterations and the momentum factor made it use 0.95 to make smoother calculation of gradient.

- Random seed: With random seed 42 set globally to algorithm_globals for reproducibility. random_seed.
This Iris dataset was taken from the Scikit-learn library. We preprocessed the dataset to standardize features and conducted binary classification for all but one class. A training set was further split with an 80/20 train-test ratio

- Callback: we implemented a custom deep unfolding callback to adapt the learning rate and perturbation on-line during optimization. This function performed gradient adjustments using momentum and plotted the objective function, learning rate & perturbation values after each iteration.

- Deep unfolding: The model was deep unfolded taking 10 iterations and metrics like training and test accuracy, learning rate, perturbation were stored at each iteration The time it took to train was also recorded and shown on the results.

- Results logging: results were saved in a CSV file (dvqc_training_results.csv). csv on every iteration for elaborated analysis later.

The system setup served as a thorough and replicable setting to test the performance of VQC on deep unfolding optimizations.
