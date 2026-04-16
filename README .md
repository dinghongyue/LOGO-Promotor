# Evaluating Biological Knowledge Integration for Human Promoter Prediction (LOGO)

This repository contains code and pre-trained weights for a BMI5111 Capstone Project. The project evaluates whether integrating prior biological knowledge into the LOGO genomic language model improves human promoter prediction performance.

Two modules are included:

* Module 01: baseline promoter prediction using sequence features only
* Module 02: knowledge-augmented model incorporating GenBank functional annotations



### Citation

@article{Yang2022logo,
title={Integrating convolution and self-attention improves language model of human genome for interpreting non-coding regions at base-resolution},
author={Meng Yang, Lichao Huang, Haiping Huang, Hui Tang, Nan Zhang, Huanming Yang, Jihong Wu, Feng Mu},
journal={Nucleic Acids Research},
doi={10.1093/nar/gkac326},
year={2022},
publisher={Oxford University Press}
}



### Usage



#### Requirement

System:
Windows 10

Environment:
Python              3.10
TensorFlow          2.15.1
Keras               2.15.0
GPU                 NVIDIA RTX 3050 (4GB VRAM)



#### Installation

pip install -r requirements.txt



### Pre-training model weights

Check out the folder "99\_PreTrain\_Model\_Weight"

* LOGO 3-mer model
* LOGO 5-mer model



### Promoter Prediction

Check out the file "02\_LOGO\_Promoter/README.txt"

1. Data preparation
* Promoter sequences (TATA+, TATA-, Both) are sourced from EPDnew database
* Generate tfrecord:
python 00\_EPDnew\_data\_prepare.py
2. Train baseline model
* python 01\_PromID\_trainer.py
3. Evaluate model without retraining
* Comment out model.fit(...)
* Run model.evaluate(...)



### Knowledge-Augmented Promoter Prediction

Check out the file "02\_LOGO\_Promoter/README.txt"

1. Train knowledge-augmented model
* python 02\_PromID\_trainer\_knowledge.py
2. Knowledge terms used:
CDS, exon, enhancer, insulator, conserved region,
protein binding site, pseudogene, DNAseI hypersensitive site,
nucleotide cleavage site, silencer, gene

Note: promoter annotation is excluded to avoid label leakage



### Training Configuration

* Optimizer: Adam
* Learning rate: 1e-4
* Early stopping patience: 3
* Cross-validation: 10-fold
* Batch size:

  * 32 (baseline)
  * 16 (knowledge-augmented)





### Additional Modules

This project focuses on promoter prediction. Other LOGO modules are not included.



### Pre-trained model weights

* 99\_PreTrain\_Model\_Weight

