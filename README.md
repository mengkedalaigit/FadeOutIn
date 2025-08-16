# 🎵 Speech Augmentation for ASR Task Based on NeMo Toolkit
This repository provides a set of audio perturbations for Automatic Speech Recognition (ASR), designed to work with NVIDIA NeMo 1.6.2.
All augmentations operate directly on AudioSegment objects.

| Augmentation      | Description                                              |
| ----------------- | -------------------------------------------------------- |
| `speed`           | Resample without pitch preservation                      |
| `time_stretch`    | Phase vocoder, pitch-preserving                          |
| `gain`            | Random loudness change                                   |
| `impulse`         | Convolution with Room Impulse Responses (RIR)            |
| `shift`           | Temporal shifting with zero padding                      |
| `noise`           | Additive noise (from dataset)                            |
| `white_noise`     | White Gaussian noise                                     |
| `rir_noise_aug`   | RIR + foreground/background noise                        |
| `transcode_aug`   | Codec artifacts (G711, AMR-NB, OGG)                      |
| `random_segment`  | Random crop/pad for SSL                                  |
| **`fade_in_out`** | 🔬 **Our proposed method** – smooth fade-out and fade-in |


# 🔬 Our Contribution: FadeOutIn Perturbation

FadeOutIn (a.k.a. FadeInOutPerturbation) is a novel augmentation proposed in this work.

Idea: Speech loudness depends on the amplitude envelope, which decays with distance.
Implementation: Random segments are selected; each fades out smoothly and then fades in again.

Advantage:
More realistic than hard time masking
Retains partial spectral information
Simulates speaker–microphone movement
Improves model robustness to recording conditions
