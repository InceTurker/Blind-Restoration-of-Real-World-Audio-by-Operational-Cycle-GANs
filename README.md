
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

![364](https://user-images.githubusercontent.com/117115792/209510018-f295f4af-d2e1-444e-b569-090a485ca73e.png)

Clean Signal: 

https://user-images.githubusercontent.com/117115792/209516053-e1cdbf02-b260-48b0-9de8-cc74babafbdc.mp4

Corrupted Signal:

https://user-images.githubusercontent.com/117115792/209516106-21149458-d484-44ca-95b3-f6292cc795e5.mp4

Restored Signal:

https://user-images.githubusercontent.com/117115792/209516153-dabeb088-ab9c-4963-9c65-94c3524e8ced.mp4

![7](https://user-images.githubusercontent.com/117115792/209510044-2fde7e8c-9151-4b79-bc05-202a3ee8b9c2.png)

Clean Signal:

https://user-images.githubusercontent.com/117115792/209516240-995b3842-820f-479c-b901-1d30fe112c57.mp4

Corrupted Signal:

https://user-images.githubusercontent.com/117115792/209516255-ec9a791e-9e28-4465-92ce-c40db6671619.mp4

Restored Signal:

https://user-images.githubusercontent.com/117115792/209516266-f7b7a368-df33-41c2-a102-501876b1d7c7.mp4

![76](https://user-images.githubusercontent.com/117115792/209510078-9721d1a2-6bf7-4667-a2a1-7b7f22ac0446.png)

Clean Signal:

https://user-images.githubusercontent.com/117115792/209516352-0e7ee26e-cefa-44fc-86b0-7bbeab67b2ed.mp4

Corrupted Signal:

https://user-images.githubusercontent.com/117115792/209516361-d9d77eca-62c0-49ae-acda-7f9c4430dabf.mp4

Restored Signal:

https://user-images.githubusercontent.com/117115792/209516370-9550b184-15b1-4d21-ba80-b25cff7fa19b.mp4

![86](https://user-images.githubusercontent.com/117115792/209510106-a85680e9-7933-42b8-b219-5b5bf97b59ff.png)

Clean Signal:

https://user-images.githubusercontent.com/117115792/209516472-f01d422f-a44a-471f-9e7c-18b74b57eb76.mp4

Corrupted Signal:

https://user-images.githubusercontent.com/117115792/209516481-baa50b75-7510-4264-8bcd-9550050d1fd9.mp4

Restored Signal:

https://user-images.githubusercontent.com/117115792/209516487-d70342a9-f1fd-43a0-ae2f-e8954f3bb0cb.mp4

![27](https://user-images.githubusercontent.com/117115792/209510128-95aa7880-07c9-45d1-ace3-65a13d28b0fa.png)

Clean Signal:

https://user-images.githubusercontent.com/117115792/209516546-c8f2b886-33de-48e3-8c5b-c43dccc596f9.mp4

Corrupted Signal:

https://user-images.githubusercontent.com/117115792/209516560-21ba4d60-0733-49ba-8841-d8e34b5b6e73.mp4

Restored Signal:

https://user-images.githubusercontent.com/117115792/209516569-7d0bf58b-99f5-4162-84b9-b7562ba2edf3.mp4

![32](https://user-images.githubusercontent.com/117115792/209510142-75efddbd-483f-4df0-8ded-1e12b39b13a7.png)

Clean Signal:

https://user-images.githubusercontent.com/117115792/209516633-4586be01-98d1-47ca-9864-223eb130da69.mp4

Corrupted Signal:

https://user-images.githubusercontent.com/117115792/209516644-fb511f32-4c2a-40a1-9ff1-55104b9cb48d.mp4

Restored Signal:

https://user-images.githubusercontent.com/117115792/209516657-6239ef67-370b-4853-a63b-61a2d19b5ef0.mp4

## Citation
If you find this project useful, we would be grateful if you cite this paper：

```http

```
