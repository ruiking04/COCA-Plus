# COCA+: Robust Contrastive One-class Time Series Anomaly Detection with Contaminated Data
This repository provides the implementation of the _COCA+: Robust Contrastive One-class Time Series Anomaly Detection with Contaminated Data_ method, called _COCA+_ below. 

## Abstract
> The accumulation of time-series signals and the absence of labels make time-series Anomaly Detection (AD) a self-supervised 
> task of deep learning. Most methods based on normality assumptions face the following two challenges: 
> (1) a single assumption could hardly characterize the whole normality or lead to some deviation, 
> e.g. Contrastive Learning (CL) methods distance negative pairs, many of which consist of both normal samples, thus reducing the AD performance. 
> (2) their basic assumption is that the training data is uncontaminated (free of anomalies), which is unrealistic in practice. 
> When the proportion of contaminated data increases, the performance will be affected to varying degrees. 
> This paper proposes a novel and robust approach based on multiple normality assumptions for time series anomaly detection with contaminated data. 
> We fuse the assumptions of one-class classification and contrastive learning in a single learning process to characterize a more complete so-called normality.
> Meanwhile, we introduce the idea of outlier exposure in the latent space, which helps exclude the influence of abnormal samples 
> while utilizing the contained anomaly knowledge. Boundaries become clearer by pushing potential anomalies away from clusters of normal samples. 
> Extensive experiments on four real-world time-series datasets show the superior performance of the proposed method achieves state-of-the-art.



## Citation
Link to our paper [here]().
If you use this code for your research, please cite our paper:

```
We will add citation information later.
```

## Installation
This code is based on `Python 3.8`, all requirements are written in `requirements.txt`. Additionally, we should install `saleforce-merlion v1.1.1` and `ts_dataset` as Merlion suggested.

```
pip install salesforce-merlion==1.1.1
pip install -r requirements.txt
```

## Dataset
We acknowledge the contributors of the dataset, including AIOps, UCR, SWaT, and WADI.
This repository already includes Merlion's data loading package `ts_datasets`.

### AIOps (KPI, IOpsCompetition) and UCR. 
1. AIOps Link: https://github.com/NetManAIOps/KPI-Anomaly-Detection
2. UCR Link: https://wu.renjie.im/research/anomaly-benchmarks-are-flawed/ 
and https://www.cs.ucr.edu/~eamonn/time_series_data_2018/UCR_TimeSeriesAnomalyDatasets2021.zip
3. Download and unzip the data in `data/iops_competition` and `data/ucr` respectively. 
e.g. For AIOps, download `phase2.zip` and unzip the `data/iops_competition/phase2.zip` before running the program.

### SWaT and WADI. 
1. For SWaT and WADI, you need to apply by their official tutorial. Link: https://itrust.sutd.edu.sg/itrust-labs_datasets/dataset_info/
2. Because multiple versions of these two datasets exist, 
we used their newer versions: `SWaT.SWaT.A2_Dec2015, version 0` and `WADI.A2_19Nov2019`.
3. Download and unzip the data in `data/swat` and `data/wadi` respectively. Then run the 
`swat_preprocessing()` and `wadi_preprocessing()` functions in `dataloader/data_preprocessing.py` for preprocessing.


## Repository Structure

### `conf`
This directory contains experiment parameters for all models on AIOps (as `IOpsCompetition` in the code), UCR, SWaT, and WADI datasets.

### `models`
Source code of CutAddPaste model.

### `results`
Directory where the experiment result is saved.

## COCA+ Usage
```
# COCA+ Method (dataset_name: IOpsCompetition, UCR, SWaT, WADI)
python coca+.py --selected_dataset <dataset_name> --device cuda --seed 2
```

## Baselines
Anomaly Transformer(AnoTrans, AOT), AOC, RandomScore(RAS), NCAD, LSTMED, OC_SVM, IF, SR, RRCF, SVDD, DAMP, TS_AD(TCC)

We reiterate that in addition to our method, the source code of other baselines is based on the GitHub source code 
provided by their papers. For reproducibility, we changed the source code of their models as little as possible. 
We are grateful for the work on these papers.

We consult the GitHub source code of the paper corresponding to the baseline and then reproduce it. 
For baselines that use the same datasets as ours, we use their own recommended hyperparameters. 
For different datasets, we use the same hyperparameter optimization method Grid Search as our model to find the optimal hyperparameters.

### Acknowledgements
Part of the code, especially the baseline code, is based on the following source code.
1. [Anomaly Transformer(AOT)](https://github.com/thuml/Anomaly-Transformer)
2. [AOC](https://github.com/alsike22/AOC)
3. [Deep-SVDD-PyTorch](https://github.com/lukasruff/Deep-SVDD-PyTorch)
4. [TS-TCC](https://github.com/emadeldeen24/TS-TCC)
5. [DAMP](https://sites.google.com/view/discord-aware-matrix-profile/documentation) and 
[DAMP-python](https://github.com/sihohan/DAMP)
6. LSTM_ED, SR, and IF are reproduced based on [saleforce-merlion](https://github.com/salesforce/Merlion/tree/main/merlion/models/anomaly)
7. [RRCF](https://github.com/kLabUM/rrcf?tab=readme-ov-file)
8. [Metrics:affiliation-metrics](https://github.com/ahstat/affiliation-metrics-py)

