# Two_Part-Audio_DeepfakeDetection - Version2

This repository contains the implementation for two-part architecture using fundamental frequency, dominant frequency and spectral features.
![image](https://user-images.githubusercontent.com/61777099/194679033-9c61bc9f-9bc6-415e-be1e-579ac4109d8c.png)


## Instructions

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


EER values for the proposed model and the baseline models provided by ASVSpoof2019 organizers:
    https://arxiv.org/pdf/2102.05889.pdf

| Model                   | EER value    | min-tDFC    |   
| ------------------------|:-------------|:-------------|
| Proposed Model - Fundamental_Dominant Frequency | 4.27| 0.1271  |
| GMM - LFCC features     |  3.50 |    0.0904|
| LCNN - LFCC feature     |  5.06 |        0.1000|


# In progress

CQCC is another promising audio feature computed by Constant Q transform which outlines the background structure of the audio files as an alternative tyo Fourier transform. Currently, I am working on CQCC feature along with spectral features such as mean and std of frequency, skew and spectral entropy. Spectral features are statistical analysis of the audio samples thus outlining the backbone structure of the audio.

