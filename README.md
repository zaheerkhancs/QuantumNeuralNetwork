# ROC Curve
<img align="left" src="https://github.com/zaheerkhancs/QuantumNeuralNetwork/blob/master/roc.png" width=300px>
# Confusion Matrix
<img align="left" src="https://github.com/zaheerkhancs/QuantumNeuralNetwork/blob/master/confusion.png" width=300px>
# Fraud detection

This folder provides the source code used in Experiment B in *"Continuous-variable quantum neural networks"* [arXiv:1806.06871](https://arxiv.org/abs/1806.06871).

## Getting the data

The raw data is sourced from the [Credit Card Fraud Detection](https://www.kaggle.com/mlg-ulb/creditcardfraud) dataset on Kaggle. The `creditcard.csv` file should be downloaded and placed in this folder. The user can then run:
```bash
python3 data_processor.py
```
This script creates two datasets for training and testing.

## Training and testing the model

The model is a hybrid classical-quantum classifier, with a number of input classical layers that control the parameters of an input layer in a two-mode CV quantum neural network. The model is trained so that it outputs a photon in one mode for a genuine credit card transaction, and outputs a photon in the other mode for a fraudulent transaction.

Training can be performed with:
```bash
python3 fraud_detection.py
```
| WARNING: this script can take a long time to run. On a typical PC, it may take hours to arrive at a well-trained model. |
| --- |

The model is periodically saved during training, and progress can be monitored by launching TensorBoard in the terminal:
```bash
tensorboard --logdir=outputs/tensorboard/simulation_label
```
where `simulation_label` is the name used to refer to a particular run of the script `fraud_detection.py` (this is specified within the file itself; the default is `1`).

Testing can be performed with:
```bash
python3 testing.py
```
| WARNING: this script can take a long time to run|
| --- |

## Visualizing the results

The performance of the trained model can be investigated with:
```bash
python3 roc.py
```
which outputs the receiver operating characteristic (ROC) curve and confusion matrix for the optimal threshold probability.


## Model dependency
1. python 3.5
2. tensorflow <=1.3.0
3. strawberryfields <=1.10.0 ## higher version would't run the script
4. scipy 
5. numpy
6. pip 1.18.0
7. Ubuntu 16.0

