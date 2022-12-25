
# Project Description

Objective: Despite numerous studies proposed for audio restoration in the literature, most of them focused on an isolated restoration problem such as denoising or dereverberation, ignoring the other artifacts. Moreover, assuming a limited number of signal-to-distortion ratio (SDR) levels is a common practice. However, real-world audio is often corrupted by a blend of artifacts such as reverberation, sensor noise, and background audio mixture with varying types, severities, and duration. In this study, we propose a novel approach for blind restoration of real-world audio signals by Operational Generative Adversarial Networks (Op-GANs) with temporal and spectral objective metrics to enhance the quality of restored audio signal regardless of the type and severity of each artifact corrupting it. Methods: 1D Operational-GANs are used with the generative neuron model optimized for blind restoration of any corrupted audio signal. Results: The proposed approach has been evaluated extensively over the benchmark TIMIT-RAR (speech) and GTZAN-RAR (non-speech) datasets corrupted with a random blend of artifacts each with a random severity to mimic real-world audio signals. Average SDR improvements over 7.2 dB and 4.9 dB are achieved, respectively. Significance: This is a pioneer study in blind audio restoration with the unique capability of direct (time-domain) restoration of real-world audio whilst achieving an unprecedented level of performance for a wide SDR range and artifact types. Conclusion: 1D Op-GANs can achieve robust and computationally effective real-world audio restoration with an elegant performance level.
[Paper Link](https://arxiv.org/abs/2202.00589)

![image](https://user-images.githubusercontent.com/117115792/209479770-85f967b7-91f9-42f6-af34-08a3412bba1f.png)

## Real-World Audio Dataset 


![image](https://user-images.githubusercontent.com/117115792/209479487-75c1f71b-cf0b-46b3-a60a-c282a856244f.png)

- The proposed formation of both benchmark datasets generated in this study to mimic real-world corrupted audio clips is illustrated in Figure.  
To accomplish this aim, the outputs of randomly selected degradation sources are randomly (~U [0,1]) weighted before corrupting the clean target audio. The two artifacts (AWGN and background mixture) are additive while a linear convolution is applied for reverberation. Therefore, linear (random) weights can be used to control the weights of each artifact type selected. In addition to the random blend of all artifacts, we manually created single artifact cases (only one of is turned on) to be included in the final datasets, which may correspond to the scenarios where only background mixture or reverberation exist. 
 - For the evaluation of speech restoration, a total of 2703 clean data samples are
taken from the [TIMIT Corpus Dataset](https://catalog.ldc.upenn.edu/LDC93s1),which contains recordings of different speakers from 8 major dialects of American English each reading phonetically rich sentences. Each utterance is a 2-second-long (32000 samples) segment with a sampling rate of 16 kHz. For the
training and validation sets, 2000 randomly selected data samples are input to the real-world corrupted audio generation setup. The
final train set includes 1500 samples from the blend of all artifacts as well
as 500 samples per single artifact case, which adds up to a total of 3000 data
samples. Note for each single artifact case samples are selected as
non-overlapping groups (of 500 samples) from randomly selected 1500 train
samples. Similarly, 500 and 703 randomly selected utterances from the remaining
data are used to form the independent validation and test sets, which includes a
total of 1000 and 1453 data samples, respectively. This benchmark dataset that
can henceforth be used for real-world audio restoration is named TIMIT-RAR. 

- Similarly, forthe evaluation of non-speech audio restoration, approximately
1.45-second-long segments (32000 samples with a sampling rate of 22050 Hz) from
the classical and jazz music recordings of the [GTZAN Music dataset](https://www.kaggle.com/datasets/andradaolteanu/gtzan-dataset-music-genre-classification) are used. The
final train set includes 1750 samples from the blend of all artifacts as well
as 500 samples (as non-overlapping groups) per single artifact cases, which
adds up to a total of 3250 data samples. Similarly, 500 and 830 randomly
selected utterances from the remaining data are used to form the independent
validation and test sets, which includes a total of 1000 and 1660 data samples,
respectively. This benchmark dataset that can henceforth be used for real-world
audio restoration is named GTZAN-RAR. The final train, validation, and test
data compositions of both datasets are given in Table 1.

- [TIMIT-RAR Dataset](http://2020.icbeb.org/CSPC2020) and [GTZAN-RAR Dataset](http://2020.icbeb.org/CSPC2020) can be downloaded from given links.

## Run

#### Train
- Download train data to the "mats/" folder
- Start training
```http
  python 1D_Self_Operational_CycleGAN.py
```
- Start evaluation. You can download Pre-trained Network [weights](https://drive.google.com/drive/folders/1ezrWa6A69H5ccNV1y2hb_GuyLsmEk1ff?usp=sharing)
```http
  python test.py
```
- Save outputs to the "test_outputs/" folder 
- Visualize Results
```http
  python plot_outputs.py
```
## Prerequisites
- Pyton 3
- Pytorch
- [FastONN](https://github.com/junaidmalik09/fastonn) 


  
## Results


Clean Signal:
Corrupted Signal:
Restored Signal:


Clean Signal:
Corrupted Signal:
Restored Signal:


Clean Signal:
Corrupted Signal:
Restored Signal:


Clean Signal:
Corrupted Signal:
Restored Signal:


Clean Signal:
Corrupted Signal:
Restored Signal:


Clean Signal:
Corrupted Signal:
Restored Signal:

## Citation
If you find this project useful, we would be grateful if you cite this paper：

```http
Kiranyaz S, Devecioglu OC, Ince T, Malik J, Chowdhury M, Hamid T, Mazhar R, Khandakar A, Tahir A, Rahman T, Gabbouj M. Blind ECG Restoration by Operational Cycle-GANs. IEEE Trans Biomed Eng. 2022 Dec;69(12):3572-3581. doi: 10.1109/TBME.2022.3172125. Epub 2022 Nov 21. PMID: 35503842.
```
