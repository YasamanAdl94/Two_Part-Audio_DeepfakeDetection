# Two_Part-Audio_DeepfakeDetection - Version2

This repository contains the implementation for two-part architecture using fundamental frequency, dominant frequency and spectral features.
![Diagram2](https://user-images.githubusercontent.com/61777099/203357688-d8b3b118-5d5e-48fc-aab2-61db5ef4b0c2.png)


## Instructions

I have used Pycharm IDE for this project and created a virtual environment with required packages. You have the option of creating a conda environment as Python interpreter instead if needed.  The python version I am using in my env is 3.7.9.

    $ conda install pytorch torchvision torchaudio cudatoolkit=11.1 -c pytorch -c nvidia
    $ pip install -r requirements.txt

## Libraries used and their licenses

    Librosa: ISC License
    Soundfile: BSD License (BSD 3-Clause License)
    Spafe: BSD License (BSD)
    
   
### Dataset
ASVSpoof2019 dataset has been used in this project. The dataset is available at:
     https://datashare.ed.ac.uk/handle/10283/3336

The Logical Access (LA) category has been used for this project. Development set is used for validation and evaluation set is used for testing purposes.

### Training
To train the model run:

    python main.py 
   
   
**you need to change the default database_path and protocols_path inside the code to the ASVSpoof2019 directory or include it as command line arguments (--database_path/--protocols_path)**


Other hyperpramater values such as epoch numbers, batch_size, learning rate and etc. are set as default in the code but can be changed if given as the command line argument e.g. --num_epochs=200


### Testing

    python main.py --is_eval --eval --model_path='/path/to/your/best_model.pth' --eval_output='eval_scores_file.txt'

### Computing EER value

    python tDCF_python/evaluate_tDCF_asvspoof19_eval_LA.py Eval 'eval_scores_file.txt'
    

EER values for the proposed model and the baseline models provided by ASVSpoof2019 organizers:
    https://arxiv.org/pdf/2102.05889.pdf

| Model                   | EER value   % | min-tDFC    |   
| ------------------------|:-------------|:-------------|
| **Proposed Model - Fundamental_Dominant Frequency** | **4.269**| **0.12712**  |
| GMM - LFCC features     |  3.50 |    0.0904|
| LCNN - LFCC feature     |  5.06 |        0.1000|


# In progress

CQCC is another promising audio feature computed by Constant Q transform which outlines the background structure of the audio files as an alternative to Fourier transform. Currently, I am working on CQCC feature along with spectral features such as mean and std of frequency, skew and spectral entropy. Spectral features are statistical analysis of the audio samples thus outlining the backbone structure of the audio. Background noise is related to spectral features of the audio so I believe I can do audio forensics analysis using these features.

1. CQCC Features

2. Computed from Constant Q transform used for time-frequency analysis of audio samples

3. Spectral Features

4. Background noise - Track 1 in ADD dataset

5. Acoustic Scene

6. Electric Network Frequency Signal

7. GAT model ensemble with Bilevel optimization


