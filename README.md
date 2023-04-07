eeg_challenge_code
================================
This is the codebase for the [eeg_challenge_code](https://www.xfyun.cn/).
This codebase contains baseline models and code to preprocess stimuli.

# Prerequisites

Python >= 3.6

# General setup

Steps to get a working setup:

## 1. Clone this repository and install the [requirements.txt](requirements.txt)
```bash
# Clone this repository
git clone https://github.com/zqs01/eeg_challenge_code.git

# Go to the root folder
cd eeg_challenge_code

# Install requirements.txt
python3 -m install requirements.txt
```

## 2. Download the data 

   1. `split_data(.zip)` contains already preprocessed, split and normalized data; ready for model training/evaluation. 
If you want to get started quickly, you can opt to only download this folder/zipfile.

   2. `preprocessed_eeg(.zip)` and `preprocessed_stimuli(.zip)` contain preprocessed EEG and stimuli files (envelope and mel features) respectively.
At this stage data is not yet split into different sets and normalized. To go from this to the data in `split_data`, you will have to run the `speech_features.py` script ([create_data/speech_features.py](create_data/speech_features.py)) .

   3. `raw_eeg(.zip)` and `stimuli(.zip)` contain the raw EEG and stimuli files. If you want to process the stimuli files, you can run `split_and_normalize.py`  ([create_data/split_and_normalize.py](create_data/split_and_normalize.py)). The processed stimuli files will be stored in the `processed_stimuli` folder.
Currently, no preprocessing code is made available to preprocess EEG, so you will have to write your own implementation or use the precomputed `processed_eeg` folder.

## 3. Adjust the `config.json` accordingly

 `config.json` defining the folder names and structure for the data ([util/config.json](util/config.json)).
Adjust `dataset_folder` in the `config.json` file from `null` to the absolute path to the folder containing all data.


OK, you should be all setup now!

​    

# Running the task

The task has already some ready-to-go experiments files defined to give you a baseline and make you acquainted with the problem. The experiment files live in the `experiment` subfolder. The training log, best model and evaluation results will be stored in a folder called `results_{experiment_name}`.



## Regression (reconstructing envelope from EEG)

By running [experiments/linear_baseline.py](experiments/linear_baseline.py), you can train and evaluate a simple linear baseline model with Pearson correlation as a loss function, similar to the baseline model used in [Accou et al (2022)](https://www.biorxiv.org/content/10.1101/2022.09.28.509945).

By running [experiments/vlaai.py](experiments/vlaai.py), you can train/evaluate the VLAAI model as proposed by [Accou et al (2022)](https://www.biorxiv.org/content/10.1101/2022.09.28.509945). You can find a pre-trained model at [VLAAI's github page](https://github.com/exporl/vlaai).

Other models you might find interesting are: [Thornton et al. (2022)](https://iopscience.iop.org/article/10.1088/1741-2552/ac7976),...

# Special Thanks

The code for this repository comes from[auditory-eeg-challenge-2023-code](https://github.com/exporl/auditory-eeg-challenge-2023-code), so you can also refer to the description of their repository. If you have questions, you are welcome to ask in our repository.