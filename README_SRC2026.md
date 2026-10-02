# Physics-Aware AI for Radar Sensing: SRC Annual Review 2026

Posters and demo videos presented by the NC State radar group (PI: Dr. Sevgi Z. Gurbuz, Department of Electrical & Computer Engineering) at the SRC Annual Review 2026, Georgia Tech. <!-- TODO: add event dates and the SRC center/theme name -->

**Award:** Best Simulation Poster Award <!-- TODO: say which poster won -->

The three posters share one application: finding and assessing survivors in disaster response, where there is no light, no line of sight, and no ground truth data.

## Posters

| # | Title | Authors | File |
|---|-------|---------|------|
| 2.1 | Radar-based Heart-Rate Sensing in Emergency Response Scenarios | Muhammad Moiz, Sultanus Salehin | [PDF](posters/2.1_heart_rate_sensing.pdf) · [PPTX](posters/2.1_heart_rate_sensing.pptx) |
| 2.2 | Physics-Aware Machine Learning for Real-World Human Activity Recognition | Kamrul Islam, Sultanus Salehin | [PDF](posters/2.2_human_activity_recognition.pdf) · [PPTX](posters/2.2_human_activity_recognition.pptx) |
| 2.9 | Physics-Aware AI for Adaptive In-Situ Learning in Radar-based ATR | Sultanus Salehin, Sean Kearney, Kamrul Islam, Muhammad Moiz, Sevgi Z. Gurbuz | [PDF](posters/2.9_adaptive_in_situ_learning_atr.pdf) · [PPTX](posters/2.9_adaptive_in_situ_learning_atr.pptx) |

### 2.1 Heart-rate sensing under body motion

A trapped survivor does not hold still, and body motion is far stronger than the chest motion caused by a heartbeat. A radar skeleton estimator (CAE + Bi-LSTM) tracks 14 body keypoints from range-azimuth, range-elevation, and range-Doppler maps. Subtracting the estimated skeleton motion from the radar phase leaves respiration and heartbeat. The model is supervised by the radar's own micro-Doppler envelopes, not optical ground truth.

- 0.88 s latency and 35.69 J per inference on an Intel Core Ultra 7 268V
- About 20x less energy than A-VMD (711.76 J)
- Lowest peak memory (175 MB) among the evaluated methods
- Sensors: 77 GHz AWR2243 mmWave radar and 10 GHz Vayyar Walabot UWB radar

### 2.2 Human activity recognition

Two physics-aware models address the two main roadblocks, pre-processing cost and limited data.

- **CV-SincNet** classifies directly from the raw complex I/Q signal. Each learned band-pass filter corresponds to a velocity band, so no spectrogram is formed. 0.54 M parameters, about 1 s end to end, over 20x faster pre-processing than spectrogram pipelines.
- **PhGAN + CAE** generates synthetic training data with envelope constraints that keep the samples kinematically plausible. 92% accuracy with 2.4 M parameters, compared with 82% for ViT-B/16 at 85.8 M parameters.
- Dataset: 12 activity classes (9 gaits, 3 in-place), 6 participants, 77 GHz FMCW radar

### 2.9 Adaptive in-situ learning for ATR

Continuous Prototype Learning (CPL) with a physics-aware multi-task backbone (PhyMTL). When the radar meets an unknown target, it creates a new prototype for it instead of forcing a wrong label, and it learns the new class without forgetting the old ones. Applications shown are counter-UAS and through-the-wall human sensing.

- 29% lower skeleton error from the physics-aware loss alone
- Skeleton estimation learned in-situ from radar data, with no prior real data

## Demo videos

| Demo | Related poster | Video |
|------|----------------|-------|
| CV-SincNet activity recognition | 2.2 | [demos/CVSincNet_demo_video.mp4](demos/CVSincNet_demo_video.mp4) |
| Continuous Prototype Learning (CPL) | 2.9 | [demos/CPL_demo_video.mp4](demos/CPL_demo_video.mp4) |

The CV-SincNet video shows real-time activity prediction from a 77 GHz radar, with the live GUI next to the camera view. The CPL video walks through continual learning: a base set of users and activities is learned offline, then new ones are added on the fly without forgetting the old ones.

## Repository layout

```
posters/   poster files (PDF and PPTX)
demos/     recorded demo videos
```

## Team

Sultanus Salehin, Kamrul Islam, Muhammad Moiz, Sean Kearney, Nazifa <!-- TODO: full name and role -->, Dr. Sevgi Z. Gurbuz (PI)

## Acknowledgment

This work was supported by the Semiconductor Research Corporation (SRC). <!-- TODO: add center name and task ID as required by SRC -->

## Contact

<!-- TODO: contact name and email -->
