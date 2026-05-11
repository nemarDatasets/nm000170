[![DOI](https://img.shields.io/badge/DOI-10.82901%2Fnemar.nm000170-blue)](https://doi.org/10.82901/nemar.nm000170)

# BNCI 2025-002 Continuous 2D Trajectory Decoding dataset

BNCI 2025-002 Continuous 2D Trajectory Decoding dataset.

## Dataset Overview

- **Code**: BNCI2025-002
- **Paradigm**: imagery
- **DOI**: 10.1088/1741-2552/ac689f
- **Subjects**: 10
- **Sessions per subject**: 3
- **Events**: snakerun=1, freerun=2, eyerun=3
- **Trial interval**: [0, 8] s
- **Runs per session**: 3
- **File format**: gdf
- **Data preprocessed**: True

## Acquisition

- **Sampling rate**: 200.0 Hz
- **Number of channels**: 60
- **Channel types**: eeg=60, eog=4
- **Channel names**: AF3, AF4, AF7, AF8, AFz, C1, C2, C3, C4, C5, C6, CP1, CP2, CP3, CP4, CP5, CP6, CPz, Cz, F1, F2, F3, F4, F5, F6, F7, F8, FC1, FC2, FC3, FC4, FC5, FC6, FCz, FT7, FT8, Fz, HEOG1, HEOG2, O1, O2, Oz, P1, P2, P3, P4, P5, P6, P7, P8, PO3, PO4, PO7, PO8, POz, PPO1h, PPO2h, Pz, T7, T8, TP7, TP8, VEOG1, VEOG2
- **Montage**: af7 af3 afz af4 af8 f7 f5 f3 f1 fz f2 f4 f6 f8 ft7 fc5 fc3 fc1 fcz fc2 fc4 fc6 ft8 t7 c5 c3 c1 cz c2 c4 c6 t8 tp7 cp5 cp3 cp1 cpz cp2 cp4 cp6 tp8 p7 p5 p3 p1 pz p2 p4 p6 p8 ppo1h ppo2h po7 po3 poz po4 po8 o1 oz o2
- **Hardware**: actiCAP, Brain Products GmbH
- **Software**: MATLAB 2015b, Psychtoolbox, EEGLAB
- **Reference**: right mastoid
- **Ground**: Fpz
- **Sensor type**: EEG
- **Line frequency**: 50.0 Hz
- **Online filters**: anti-aliasing 25 Hz, notch 50 Hz
- **Auxiliary channels**: EOG (4 ch, horizontal, vertical)

## Participants

- **Number of subjects**: 10
- **Health status**: patients
- **Clinical population**: Healthy (able-bodied participants) + 1 SCI participant
- **Age**: mean=24.0, std=5.0
- **Gender distribution**: male=5, female=5
- **Handedness**: {'right': 10}
- **BCI experience**: naive BCI users in terms of motor decoding; 4 had previous EEG experience
- **Species**: human

## Experimental Protocol

- **Paradigm**: imagery
- **Task type**: continuous 2D trajectory decoding
- **Number of classes**: 3
- **Class labels**: snakerun, freerun, eyerun
- **Trial duration**: 23.0 s
- **Study design**: Attempted movement paradigm: participants instructed to attempt lower arm movement as if wielding a computer mouse while arm was strapped to armrest. Two task types: snakeruns (target tracking) and freeruns (self-paced shape tracing). Offline calibration followed by online feedback in 50% and 100% EEG feedback conditions.
- **Feedback type**: visual (green dot showing EEG-decoded trajectory position)
- **Stimulus type**: visual targets (white snake/shapes on black screen)
- **Stimulus modalities**: visual
- **Primary modality**: visual
- **Synchronicity**: continuous
- **Mode**: attempted movement
- **Training/test split**: True
- **Instructions**: Track snake with gaze and simultaneously attempt movement of strapped lower arm/hand as if wielding computer mouse; for freeruns: trace static shapes at own pace

## HED Event Annotations

Schema: HED 8.4.0 | Browse: https://www.hedtags.org/hed-schema-browser

```
  snakerun
    ├─ Experiment-structure
    └─ Label/snakerun

  freerun
    ├─ Experiment-structure
    └─ Label/freerun

  eyerun
    ├─ Experiment-structure
    └─ Label/eyerun

```
## Paradigm-Specific Parameters

- **Detected paradigm**: motor_imagery
- **Imagery tasks**: attempted arm/hand movement (2D continuous trajectory)

## Data Structure

- **Trials**: {'calibration_eyeruns': 38, 'calibration_snakeruns': 48, '50%_EEG_feedback_snakeruns': 36, '100%_EEG_feedback_snakeruns': 36, 'freeruns': 9}
- **Trials context**: per_paradigm_type

## Preprocessing

- **Data state**: preprocessed
- **Preprocessing applied**: True
- **Steps**: anti-aliasing filter (25 Hz), notch filter (50 Hz), downsampling to 100 Hz, bad channel interpolation, eye artifact subtraction (SGEYESUB algorithm), removal of frontal (AF) row channels, high-pass filter (0.18 Hz), common average re-reference, pops and drifts attenuation (HEAR algorithm), low-pass filter (3 Hz), downsampling to 20 Hz
- **Highpass filter**: 0.18 Hz
- **Lowpass filter**: 3.0 Hz
- **Notch filter**: [50] Hz
- **Filter type**: Not specified
- **Artifact methods**: SGEYESUB (eye artifact subtraction), HEAR (pops and drifts removal)
- **Re-reference**: common average reference
- **Downsampled to**: 20.0 Hz

## Signal Processing

- **Classifiers**: PLS regression with UKF smoothing
- **Feature extraction**: Temporal features (7 time points × 55 channels = 385 features), sLORETA (source localization)
- **Spatial filters**: Minimum norm imaging

## Cross-Validation

- **Method**: across-session
- **Evaluation type**: within-subject, learning effects over sessions

## Performance (Original Study)

- **Normalized Correlation Mean**: 0.31
- **Normalized Correlation Std**: 0.02
- **Correlation Range Rc**: 0.4-0.5
- **Nrmse Calibration**: 0.1
- **Nrmse 100% Feedback**: 0.12

## BCI Application

- **Applications**: neuroprosthesis, robotic arm control, upper limb restoration
- **Environment**: laboratory
- **Online feedback**: True

## Tags

- **Pathology**: Healthy, Spinal cord injury
- **Modality**: Visual
- **Type**: Motor attempt, Continuous decoding

## Documentation

- **Description**: Continuous 2D trajectory decoding from attempted movement: across-session performance in able-bodied and feasibility in a spinal cord injured participant
- **DOI**: 10.1088/1741-2552/ac689f
- **License**: CC-BY-4.0
- **Investigators**: Hannah S Pulferer, Brynja Ásgeirsdóttir, Valeria Mondini, Andreea I Sburlea, Gernot R Müller-Putz
- **Senior author**: Gernot R Müller-Putz
- **Contact**: gernot.mueller@tugraz.at
- **Institution**: Institute of Neural Engineering, Graz University of Technology
- **Address**: Stremayrgasse 16/IV, 8010 Graz, Austria
- **Country**: Austria
- **Repository**: GitHub
- **Data URL**: https://github.com/sccn/labstreaminglayer
- **Publication year**: 2022
- **Funding**: European Research Council ERC-CoG 2015 681231 'Feel Your Reach'; NTU-TUG joint PhD program
- **Ethics approval**: Medical University of Graz, votum number 32–583 ex 19/20
- **Keywords**: electroencephalography, trajectory decoding, learning effects, source localization, motor control, neuroplasticity, brain-computer interface

## References

Kobler, R. J., Almeida, I., Sburlea, A. I., & Muller-Putz, G. R. (2022). Continuous 2D trajectory decoding from attempted movement: across-session performance in able-bodied and feasibility in a spinal cord injured participant. Journal of Neural Engineering, 19(3), 036005. https://doi.org/10.1088/1741-2552/ac689f

Notes

.. versionadded:: 1.3.0

This dataset is designed for continuous decoding research, specifically for predicting 2D hand movement trajectories from EEG. Unlike classification-based motor imagery datasets, this dataset contains continuous trajectory labels suitable for regression-based decoders.

The paradigm "imagery" is used for compatibility with MOABB's motor imagery processing pipelines, though the actual task involves attempted (rather than imagined) movements.

See Also

BNCI2014_001 : 4-class motor imagery dataset BNCI2014_004 : 2-class motor imagery dataset
Appelhoff, S., Sanderson, M., Brooks, T., Vliet, M., Quentin, R., Holdgraf, C., Chaumon, M., Mikulan, E., Tavabi, K., Hochenberger, R., Welke, D., Brunner, C., Rockhill, A., Larson, E., Gramfort, A. and Jas, M. (2019). MNE-BIDS: Organizing electrophysiological data into the BIDS format and facilitating their analysis. Journal of Open Source Software 4: (1896). https://doi.org/10.21105/joss.01896

Pernet, C. R., Appelhoff, S., Gorgolewski, K. J., Flandin, G., Phillips, C., Delorme, A., Oostenveld, R. (2019). EEG-BIDS, an extension to the brain imaging data structure for electroencephalography. Scientific Data, 6, 103. https://doi.org/10.1038/s41597-019-0104-8

---
Generated by MOABB 1.5.0 (Mother of All BCI Benchmarks)
https://github.com/NeuroTechX/moabb
