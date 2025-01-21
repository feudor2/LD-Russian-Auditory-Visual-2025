# Visual vs Auditory Lexical Decision in Russian: Modality Makes Sense 
_The data and code for two Russian lexical decision task experiments in visual and auditory modalities_

## Abstract
_Lexical decision task_ is one of the most wide-spread methods used is psycholinguistic experiments, performed in either visual or auditory modality. The comparability of results acquired in the two modalities, however, has only recently received attention. In this paper, we present the results of two parallel experiments, one in the visual modality and one in the auditory modality, run on the same lexical material (words and pseudo-words). The reaction time distributions differ between the two modalities: mean reaction time is longer in the auditory modality. Mean reaction time for pseudo-words in significantly longer the mean reaction time for real words.

**Keywords:** lexical decision; visual modality; auditory modality; reaction time; pseudo-words

## Methods
Both visual and auditory experiments were conducted using PsychoPy software (Peirce 2007).
* The first, **visual** experiment, was conducted on 24 subjects aged 17-55; 3 were later excluded due to their low accuracy and outstanding number of outliers.
* The second, in **auditory** modality, was conducted on 26 subjects aged 18-69; 2 of them were later excluded.
  
The data was analysed with python.

## Data & Repository Contents
### Experiments Data
The initial dataset `data/LD_participants_data.csv` contains the data, assembled from the two experiments.
The main feature of the dataset is participants' reaction time `rt`.

Other features, recorded during the experiments, include:
* `subject`: a unique participant's ID
* `experiment_id`: participant's ID in the experiment
* `age`: participant's age
* `modality`: `0` for the visual experiment or `1` for the auditory one
* `word`: stimulus in its orthographic representation
* `is_correct`: the correctness of participants' responses given by key presses (`1` correct, `0` otherwise); participants' accuracy was calculated based on this parameter
* `is_test`: `1` if a record was made during test session or `0` for training session
* `is_word`: `1` if a record corresponds to a real word or `0` for a pseudoword

### Data Processing
The data preprocessing was conducted in jupyter notebook `LD_data_preprocessing.ipynb`. After completing the preprocessing procedure the dataset transforms into `data/LD_preprocessed_data.csv`, which is examined in `LD_data_analysis.ipynb` notebook.
The preprocessed dataset includes the following additional features:
* `is_outlier_word`: `1` if RT value of a record is extreme for the corresponding stimulus, `0` otherwise
* `is_outlier_word`: `1` if RT value of a record is extreme for the corresponding participant, `0` otherwise
* `is_outlier_word`: `1` if RT value of a record is extreme either for the corresponding participant or the corresponding word, `0` otherwise
* `rtz`: `rt`, standardized by both participant and stimulus
* `rtz_subject`: `rt`, standardized by participant only
* `rtz_word`: `rt`, standardized by stimulus only

### Stimuli Features
Furthermore, the dataset includes particular features of the stimuli, drawn out form `data/normal_words_features.csv` and `data/pseudowords_features.csv`.
All words and pseudowords are bisyllabic with evenly distributed stress position (on the first or the second syllable). Other parameters may vary.

In case of the real words:
* `Freq(ipm)`: logarithmic ipm frequency of a word in Russian National Corpus (Ljashevskaja, Sharoff 2009)
* `MedianValency`: median standardized value of valency (Sylvester et al 2021)
* `MeanValency`: mean standardized value of valency
* `OLD20`: mean orthographic Levenshtein distance to 20 nearest orthographic neighbours (Yarkoni et al., 2008); calculated based on (Ljashevskaja, Sharoff 2009)'s vocabulary
* `PLD20`: mean phonetic Levenshtein distance to 20 nearest phonetic neighbours; calculated based on (Ljashevskaja, Sharoff 2009)'s vocabulary transcription
* `LengthOrth`: word's length in chars
* `LengthPhon`: word's length in sounds
* `Duration`: word's recording duration
* `NormOLD`: `OLD20` divided by `LengthOrth`; calculated based on (Ljashevskaja, Sharoff 2009) 's vocabulary
* `NormPLD`: `PLD20` divided by `LengthPhon`; calculated based on (Ljashevskaja, Sharoff 2009)'s vocabulary transcription
* `OUP`: orthographic uniqueness point, 1 as the total word length (low uniqueness), or tends to 0 (greater uniqueness); calculated based on (Ljashevskaja, Sharoff 2009)'s vocabulary
* `PUP`: phonetic uniqueness point, 1 as the total word phonetic length (low uniqueness), or tends to 0 (greater uniqueness); calculated based on ((Ljashevskaja, Sharoff 2009)'s vocabulary transcription
* `StressPos`: position of the stressed syllable, `1` or `2`

In case of the pseudowords, all features are relevant, except for the `Freq(ipm)` and valency features, which are set to `NaN`.

## Infographic
### Participants' RT scores
#### Visual Modality
Words:
![alt text](https://github.com/feudor2/LD-Russian-Auditory-Visual-2025/blob/main/images/boxplots_participants_0_1.png?raw=true)
Pseudowords:
![alt text](https://github.com/feudor2/LD-Russian-Auditory-Visual-2025/blob/main/images/boxplots_participants_0_0.png?raw=true)
#### Auditory Modality
Words:
![alt text](https://github.com/feudor2/LD-Russian-Auditory-Visual-2025/blob/main/images/boxplots_participants_1_1.png?raw=true)
Pseudowords:
![alt text](https://github.com/feudor2/LD-Russian-Auditory-Visual-2025/blob/main/images/boxplots_participants_1_0.png?raw=true)

### RT Distribution
#### Comparing stimuli types:
![alt text](https://raw.githubusercontent.com/feudor2/LD-Russian-Auditory-Visual-2025/refs/heads/main/images/probability_distribution_histogram_stimuli.png)
![alt text](https://raw.githubusercontent.com/feudor2/LD-Russian-Auditory-Visual-2025/refs/heads/main/images/ecdf_stimuli.png)
#### Comparing modalities:
![alt text](https://raw.githubusercontent.com/feudor2/LD-Russian-Auditory-Visual-2025/refs/heads/main/images/probability_distribution_histogram_modalities.png)
![alt text](https://raw.githubusercontent.com/feudor2/LD-Russian-Auditory-Visual-2025/refs/heads/main/images/ecdf_modalities.png)

### RTs & Stimuli Features Correlation
#### Visual Modality
Words:
![alt text](https://github.com/feudor2/LD-Russian-Auditory-Visual-2025/blob/main/images/correlation_matrix_0_1.png?raw=true)
Pseudowords:
![alt text](https://github.com/feudor2/LD-Russian-Auditory-Visual-2025/blob/main/images/correlation_matrix_0_0.png?raw=true)
#### Auditory Modality
Words:
![alt text](https://github.com/feudor2/LD-Russian-Auditory-Visual-2025/blob/main/images/correlation_matrix_1_1.png?raw=true)
Pseudowords:
![alt text](https://github.com/feudor2/LD-Russian-Auditory-Visual-2025/blob/main/images/correlation_matrix_1_0.png?raw=true)


## Acknowledgements
We would like to express our gratitude to all subjects who took the time to participate in our experiment.

## References
1. Ljashevskaja O. N. and Sharoff S. A.  Frequency dictionary of the modern Russian language based on the materials of the Russian National Corpus. – LLC "Publishing Center Azbukovnik", 2009.
2. Peirce J. W. PsychoPy—psychophysics software in Python //Journal of neuroscience methods. – 2007. – Т. 162. – №. 1-2. – С. 8-13.
3.	Sylvester, T., Liebig, J., & Jacobs, A. M. Neural correlates of affective contributions to lexical decisions in children and adults // Scientific Reports, 11(1). — 2021. — P. 945.
4.	Yarkoni, T., Balota, D., & Yap, M. Moving beyond Coltheart’s N: A new measure of orthographic similarity // Psychonomic bulletin & review, 15(5). — 2008. — P. 971–979.

