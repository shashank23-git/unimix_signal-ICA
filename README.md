# Unmix the Signal: Audio Source Separation Using ICA

## Overview

Unmix the Signal is a signal-processing and machine-learning project that explores Independent Component Analysis (ICA) to separate multiple audio sources from mixed recordings.

The project uses male speech, female speech, and instrumental music to create synthetic audio mixtures. A FastICA algorithm implemented from scratch using NumPy is then used to recover the original sources.

A Principal Component Analysis (PCA) baseline is also implemented to compare source-recovery performance.

## Problem Statement

When multiple audio sources are recorded together, recovering the individual signals from the observed mixtures is known as blind source separation.

This project investigates how statistical independence can be used to estimate the original sources from their mixtures.

## Objectives

- Mix multiple audio sources using a linear mixing model.
- Apply centering and whitening to the mixed signals.
- Implement FastICA from scratch using NumPy.
- Recover the individual audio components.
- Compare ICA with a PCA baseline.
- Evaluate source recovery using absolute Pearson correlation.
- Investigate performance under different mixing matrices.

## Mathematical Model

The mixing process is represented by:

X = A × S

Where:

- X represents the observed mixed signals.
- A represents the mixing matrix.
- S represents the original source signals.

ICA estimates an unmixing transformation W to recover the sources:

S_estimated = W × Z

Here, Z represents the centered and whitened observations.

## Methodology

1. Load male speech, female speech, and instrumental music.
2. Convert stereo audio to mono where necessary.
3. Resample the recordings to a common sample rate.
4. Align the signals to equal lengths.
5. Generate synthetic mixtures using a mixing matrix.
6. Center the mixed signals.
7. Whiten the observations using covariance eigendecomposition.
8. Implement FastICA using a fixed-point optimization algorithm.
9. Recover the estimated independent components.
10. Implement PCA as a baseline.
11. Match recovered components to the original sources.
12. Evaluate recovery using absolute Pearson correlation.
13. Test FastICA using different mixing matrices.

## Technologies Used

- Python
- NumPy
- SciPy
- SoundFile
- Matplotlib
- Jupyter Notebook

## Experimental Results

The initial experiment produced the following absolute correlation values after matching each recovered component to its corresponding original source.

| Original Source | PCA | FastICA |
|---|---:|---:|
| Male Speech | 0.992418 | 0.999996 |
| Female Speech | 0.990009 | 0.999999 |
| Instrumental Music | 0.996699 | 0.999997 |

FastICA achieved higher correlation with the original signals than PCA in this experiment.

These results come from a controlled experiment using known original signals and a predefined mixing matrix. They do not guarantee the same performance on arbitrary real-world recordings.

## Evaluation

Absolute Pearson correlation is used to measure the similarity between each recovered component and its corresponding original source.

Because ICA can recover sources in a different order and with different signs or amplitudes, the evaluation includes one-to-one source matching.

Correlation measures signal similarity but does not fully capture perceptual audio quality or residual interference.

## Limitations

- The experiment uses synthetic linear instantaneous mixtures.
- The method assumes that the sources are statistically independent.
- Successful recovery depends on the source signals and mixing conditions.
- ICA has permutation, sign, and scale ambiguities.
- Reverberation and time-delayed mixing are not modeled.
- Performance may vary with different audio sources and mixing matrices.

## Future Improvements

- Evaluate additional mixing matrices and source combinations.
- Test noisy and reverberant audio mixtures.
- Compare additional source-separation evaluation metrics.
- Develop an interface for uploading audio and listening to separated sources.
- Investigate more advanced source-separation techniques.

## How to Run

1. Clone or download this repository.
2. Open the Jupyter Notebook.
3. Install the required Python libraries.
4. Provide the required audio files.
5. Run the notebook cells in order.

The original audio files are not included in the repository. Provide suitable audio files locally before running the experiment.

## Conclusion

This project demonstrates a practical implementation of FastICA for audio source separation and compares its results with a PCA baseline.

The experiment highlights the role of statistical independence in recovering source signals from synthetic mixtures.
