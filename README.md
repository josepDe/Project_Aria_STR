# Scene Text Recognition with Egocentric Data from Meta Project Aria

## Introduction

This project explores Scene Text Recognition (STR) algorithms using egocentric data captured by Meta’s Project Aria glasses. The study evaluates how **lighting**, **distance**, and **resolution** influence the performance of STR algorithms, specifically:

- **EAST** for text detection  
- **CRNN** and **PyTesseract** for text recognition

This project also utilizes Project Aria’s **MPS eye-gaze tracking** to optimize processing. By identifying the "view square", a region around the user's gaze, the system applies EAST + CRNN only to this area. The processed video includes frame-by-frame text detection, recognition, and annotated output with bounding boxes and transcribed text, which is then reassembled into a new video.

### Notebooks

- **EAST analysis:** [`EAST_analysis.ipynb`](./EAST_analysis.ipynb)  
- **Text recognition (EAST + CRNN / EAST + PyTesseract):** [`text_recognition_analysis.ipynb`](./text_recognition_analysis.ipynb)  
- **Eye tracking STR analysis:** [`eye_tracking_str.ipynb`](./eye_tracking_str.ipynb)

## Key Findings

- **Resolution** and **distance** significantly affect recognition accuracy.
- **Lighting conditions** had a relatively minor impact.
- Preprocessing with **upscaling + EAST + CRNN** reduced the character error rate from **0.65** to **0.44**.
- **Brightness enhancement** often degraded performance.
- **Eye-gaze tracking** enabled efficient processing by focusing only on gaze-relevant regions.

Overall, the project identifies resolution and distance as the most critical factors affecting algorithm performance.

## Future Work

- Expand the dataset
- Implement real-time gaze-based targeting
- Analyze complex scenes in greater detail
- Evaluate additional variables such as image distortion
- Develop improved methods for merging bounding boxes
- Optimize view square sizing based on gaze position

## Custom Dataset

A custom dataset was created using Meta Project Aria glasses by recording a fixed-text poster under controlled conditions:

> **Poster Text:**  
> *"Hello world! This is Joseph testing the Meta glasses."*

### Lighting Conditions

- **Natural Lighting:** Bright but overcast daylight; no artificial lights
- **Natural + Artificial Lighting:** Daylight with bedside lamp
- **Enhanced Artificial Lighting:** Overhead + bedside lamps during daylight
- **Night-Time Lighting:** Bedside lamp only

### Capture Settings

For each lighting setup:
- Two distances: **~50 cm** and **~1 m**
- Two resolutions: **1048×1408** and **2880×2880**
- The **first frame** of each video was used for analysis

Recordings were made using custom profiles via the Meta Companion App.

## Utilities

The first-frame images used for testing can be found here:  
**TODO:** Add link

Additional data — including image specs, lighting conditions, distances, and resolutions used for each algorithm — can be found here:  
**TODO:** Add links
