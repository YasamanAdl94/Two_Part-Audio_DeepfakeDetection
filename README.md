# Two_Part-Audio_DeepfakeDetection - Version2

This repository contains the implementation for two-part architecture using fundamental frequency, dominant frequency and spectral features.



## Instructions

    $ conda install pytorch torchvision torchaudio cudatoolkit=11.1 -c pytorch -c nvidia
    $ pip install -r requirements.txt

## Libraries used and their licenses

    Librosa: ISC License
    Soundfile: BSD License (BSD 3-Clause License)
    
   
### Dataset
ASVSpoof2019 dataset has been used in this project. The dataset is available at https://datashare.ed.ac.uk/handle/10283/3336

The Logical Access (LA) category has been used for this project. Development set is used for validation and evaluation set is used for testing purposes.

### Training
To train the model run:

    python main.py 

(Other values such as epoch numbers, batch_size, learning rate and etc. are set as default but can be changed if given in the command line e.g. --num_epochs=200)

Note: The dataset path and protocols_path should be changed to the corresponding folder. The default value can be set inside the code or given as command line arguments (--database_path/--protocols_path)

### Testing

    python main.py --is_eval --eval --model_path='/path/to/your/best_model.pth' --eval_output='eval_CM_scores_file.txt'


EER values for the proposed model and the baseline models provided by ASVSpoof2019 organizers https://arxiv.org/pdf/2102.05889.pdf

| Model                   | EER value    |   
| ------------------------|:-------------|
| Proposed Model - Fundamental Frequency | 2 |     
| GMM - LFCC features     |  3.50 |    
| LCNN - LFCC feature     |  5.06 |        




