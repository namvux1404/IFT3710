# IFT3710

TITLE: Analyzing the performance of transfer learning with different EEG datasets

• First Dataset: Meditation vs thinking task

o https://openneuro.org/datasets/ds003969/versions/1.0.0

• Second Dataset: Music Listening

o https://openneuro.org/datasets/ds003774/versions/1.0.0

Team Members
- Ronnie Liu: ronnie.liu@umontreal.ca
- Anas Bourhim: anas.bourhim@umontreal.ca
- Hichem Sahraoui: hichem.sahraoui@umontreal.ca
- Van Nam Vu: van.nam.vu@umontreal.ca

Description of the Project
- Motivation:
  - Generally, in machine learning, every time there’s a different dataset, we need to
create a model that minimizes the error of validation (or test). However, with two
different EEG datasets, it can be challenging when it comes to accurately train
models in neuroscience, especially with deep learning methods. This is because
many experiments don’t have enough data due to the high complexity and cost of
the procedures for data gathering. Furthermore, preprocessing EEG data can lead
to very complex datasets (a lot of attributes for a few datapoints). We decide to
introduce the concept of transfer learning to approve the accuracy of training a
model with few EEG datapoints.

- Objectives:
  - Being able to preprocess and extract essential features for different EEG datasets
  - Understand the concept of transfer learning with different EEG datasets
  - Compare the accuracy of the dataset of music thinking between different methods
  (data training from scratch vs transfer learning)

**************************
STEPS FOR RUNNING THE CODE
**************************

PART I : RNN MODEL AND LOGISTICS REGRESSION 
- Step 1: Train the RNN Model for the music dataset (Group 1)
	-> python IFT3710/train_music.py /home/username/projects/def-sponsor00/datasets/EEG/Music_eeg_raw 1
	
- Step 2: Train the RNN Model for the music dataset (Group 2)
	-> python IFT3710/train_music.py /home/username/projects/def-sponsor00/datasets/EEG/Music_eeg_raw 2
	
- Step 3: Train the Logistics Regression Model and RNN Model for the meditation dataset
	-> python IFT3710/train_meditation.py /home/username/projects/def-sponsor00/datasets/EEG/Med_eeg_raw

TRANSFER LEARNING--
FYI : We export and save our dataset preprocessed during part I in repo Git : IFT3710/Datasets and use it for the transfer learning. So if you execute file by file in part I with salloc in Clusters, it's should be good. But in case the execution with sbatch, we save a backup dataset preprocessed in share repo of all dataset (/home/username/projects/def-sponsor00/datasets/EEG/datasets_preprocessed --> change this path in transfer_learning.py before execute)

PART II : TRANSFER LEARNING BETWEEN DATASETS (MUSIC GROUP 1 - MEDITATION)
- Step : Apply Transfer Learning from music to meditation datasets
	-> python IFT3710/transfer_learning.py 1

PART III : TRANSFER LEARNING IN ONE DATASET (MUSIC GROUP 1 - MUSIC GROUP 2)
- Step : Apply Transfer Learning from group 1 to group 2
	-> python IFT3710/transfer_learning.py 2

Xgboost

1-Update the path for the data on the participants and for the data of the daframes for the features in the Xgboost notebook

2-Run the Xgboost notebooks, you can change the hyperparameters for the model optimisation

Utilities and HdfCreation Files:
	These files are references as of how we extracted the Fourier transformation data,but the extracted csv is already in the git in the Xgboost data folder


