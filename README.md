# LSTM_CDRs
LSTM-based Generative Model to design CDR sequences

# Introduction

This code repository contains the source code for training and sampling a LSTM-based generative model for CDR sequences. Given a list of CDRs sequences (amino acid sequences), a LSTM model can be trained to learn the underlying sequence distribution. Subsequently, the user can sample from this learned distribution and generate CDR sequences. To train a model, we provide training data splitted into 4 cluster CDR sequence sets. 

# Related Work

The source code was forked from https://github.com/alexarnimueller/LSTM_peptides (Ref: A. T. Müller, J. A. Hiss, G. Schneider, "Recurrent Neural Network Model for Constructive Peptide Design" J. Chem. Inf . Model. 2018, DOI: 10.1021/acs.jcim.7b00414) and slightly adapted to be applicable to CDR sequences.

All modifications are highlighted in the code.

# Installation
## conda enviroment
Using the environment file including python 3.7:
```
conda env create -f environment.yml
```

## Virtual enviroment (pip)

Create a virtual environment with python 3.7 and install required packages from the requirements.txt
```
pip install -r requirements.txt
```

# Example Training

To train a LSTM model on CDR sequences, you can run the following command:
``````
python LSTM_CDRs.py --name Cluster1_LSTM --dataset data/Cluster1.csv --layers 2 --neurons 64 --epochs 200 --dropout 0.2
``````

Information about further parameters can be shown:
```
python LSTM_CDRs.py --help
```

# Example Sampling
To sample 10k sequences with a lengths of 36 amino acids from a trained model, you can execute the following command:
``````
python LSTM_CDRs.py --name Cluster1_LSTM --dataset Cluster1.csv --modfile Cluster1_LSTM/checkpoint/model_epoch_100.hdf5 --train False --sample 10000 -f 36 -m 36
``````

# Reference

P. Arras et al., "AI/ML combined with Next Generation Sequencing of VHH immune repertoires enables the rapid identification of de novo humanized and sequence-optimized single domain antibodies: a prospective case study", 
Front. Mol. Biosci.
Sec. Biological Modeling and Simulation
Volume 10 - 2023 | doi: 10.3389/fmolb.2023.1249247