# Shota Yamaba — @Shouta0108

**Mechanical engineering student building systems that span hardware and software** — sensors and embedded firmware on one side, signal processing, computer vision and ML on the other.

B.Eng. in Mechanical Systems Engineering, Tokyo Metropolitan University (Hase Lab) · expected Mar 2027
Tokyo, Japan · Open to new-grad roles in measurement & control, robotics/sensing, and applied ML

[![Kaggle](https://img.shields.io/badge/Kaggle-035a7d?style=for-the-badge&logo=kaggle&logoColor=white)](https://www.kaggle.com/shouta0108)
[![Sketchfab](https://img.shields.io/badge/Sketchfab-1CAAD9?style=for-the-badge&logo=sketchfab&logoColor=white)](https://sketchfab.com/Shouta0108)

---

## What I do

I like problems where the answer isn't in a library — where you have to get a signal out of noisy hardware and turn it into a number someone can act on. That thread runs through everything below: a LiDAR that returns a messy point cloud, a microphone recording where the heartbeat is buried under mains hum, a depth-camera rig that has to agree with itself across multiple viewpoints.

- **Embedded / mechatronics** — Arduino, RP2040 (dual-core), SPI displays, thermistors, serial protocols
- **Signal processing** — FFT, band-pass and notch filtering, peak detection, noise rejection
- **Vision & 3D** — OpenCV, Azure Kinect, point cloud and mesh processing, Hough transforms
- **ML & data** — PyTorch, scikit-learn, pandas/NumPy; practicing on Kaggle
- **Currently building** — a C++/Python library for point cloud, mesh and video processing

---

## 🔬 Research — Markerless gait analysis with multiple depth cameras

**Undergraduate thesis, Hase Lab, Tokyo Metropolitan University**

Clinical gait assessment (the instrumented Timed Up-and-Go, **iTUG**) normally requires a marker-based motion capture lab: expensive, slow to set up, and impossible to run in a clinic. I'm building a **markerless** alternative using **multiple time-synchronized Azure Kinect** units.

| | |
| --- | --- |
| **Problem** | Extract clinically usable gait parameters without markers or a dedicated motion-capture room |
| **Approach** | Multi-view Azure Kinect capture → time synchronization and extrinsic calibration → skeletal data fusion → musculoskeletal modeling and inverse kinematics in **OpenSim** |
| **Focus** | Quantifying how far the markerless estimate can be trusted — where multi-view fusion recovers accuracy that a single camera loses |
| **Stack** | Azure Kinect SDK, Python, OpenSim, point cloud processing |

> 📄 Paper in preparation. Code and data will be published here after submission — happy to walk through the method and results in an interview.

*Most of my day-to-day work lives in private research repositories, so the public list below is only part of the picture.*

---

## 🌍 Open Source

**[Blaizzy/mlx-vlm](https://github.com/Blaizzy/mlx-vlm)** · 5.5k★ · vision-language model inference & fine-tuning on Apple Silicon

[**#2176** — `fix: declare jinja2 as a runtime dependency`](https://github.com/Blaizzy/mlx-vlm/pull/2176) — **merged**

A clean install of the package failed at import time: `jinja2` was used at runtime but never declared, so `pyproject.toml` (which reads its dependencies from `requirements.txt`) never pulled it in. Tracing a broken install back to a packaging-metadata gap, then submitting the one-line fix upstream.

---

## 🚀 Projects

Each of these started as something I actually wanted to exist, not as a tutorial.

### [Room-simplify](https://github.com/Shouta0108/Room-simplify) · `C++` `OpenCV`
Turns raw 2D LiDAR scans into a clean floor plan.

- **Problem** — An LD19 LiDAR gives you thousands of noisy range points per revolution. A human sees "a rectangular room"; the data doesn't say that anywhere.
- **What I built** — Read the LD19's binary packet stream over USB-serial in C++, project scans into an occupancy image, then recover wall segments with a Hough line transform and merge collinear fragments into a simplified polygon.
- **Why it matters** — Runs entirely on a PC in C++ with no Raspberry Pi in the loop, so the whole pipeline from serial bytes to rendered map is one process I control end to end.

### [car-oil-water-temp-indicator](https://github.com/Shouta0108/car-oil-water-temp-indicator) · `C` `RP2040`
A real in-car gauge — oil and coolant temperature as analog-style needles on a 3.5" LCD.

- **Problem** — I wanted both temperatures on one screen in my own car, updating smoothly enough to read at a glance while driving, with warnings I couldn't miss.
- **What I built** — RP2040 firmware using **both cores**: one samples two thermistors and applies a smoothing filter, the other renders needle gauges to an ILI9486 480×320 SPI display. Staged alarms — flashing red zone above 115 °C, intermittent beep, continuous tone above 130 °C — plus a startup needle sweep.
- **Engineering detail** — Splitting sensing and rendering across cores is what removed the flicker; a single-core loop couldn't redraw fast enough while sampling.

### [detecting-heartbeat-with-microphone-sound](https://github.com/Shouta0108/detecting-heartbeat-with-microphone-sound) · `Python` `SciPy`
Estimates heart rate from a microphone recording of body sounds, without a human listening.

- **Problem** — A heartbeat recorded on a plain microphone sits under mains hum and broadband noise. Auscultation is subjective; I wanted a number.
- **What I built** — A staged pipeline: notch out power-line interference → band-pass to the 20–25 Hz heart-sound band → nonlinear peak emphasis → FFT-based search across candidate BPM values for the strongest periodicity.
- **Result** — A stable estimate of ≈63 BPM on test recordings, consistent with a plausible resting heart rate.

### [Segment-Hunter](https://github.com/Shouta0108/Segment-Hunter) · `Arduino` `C++`
A playable arcade game on a 16×2 LCD — mechatronics coursework, taken further than required.

- **What it is** — Joystick-controlled character hunting a randomly placed target against a 9-second countdown shown on a 7-segment display, with automatic level reset.
- **Why it's here** — It's the smallest complete example of the thing I keep doing: input device, state machine, and display module integrated into one responsive real-time loop.

---

## 🛠 Tech Stack

**Languages**
![C](https://img.shields.io/badge/c-%2300599C.svg?style=flat-square&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=flat-square&logo=c%2B%2B&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=flat-square&logo=python&logoColor=ffdd54)

**Embedded & Hardware**
![Arduino](https://img.shields.io/badge/-Arduino-00979D?style=flat-square&logo=Arduino&logoColor=white)
![Raspberry Pi](https://img.shields.io/badge/-Raspberry_Pi_Pico-C51A4A?style=flat-square&logo=Raspberry-Pi&logoColor=white)
![Azure Kinect](https://img.shields.io/badge/Azure_Kinect-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)

**Vision, Simulation & ML**
![OpenCV](https://img.shields.io/badge/opencv-5C3EE8.svg?style=flat-square&logo=opencv&logoColor=white)
![OpenSim](https://img.shields.io/badge/OpenSim-009688?style=flat-square)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=flat-square&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=flat-square&logo=pandas&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=flat-square&logo=scipy&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=flat-square&logo=scikit-learn&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=flat-square&logo=PyTorch&logoColor=white)
![CUDA](https://img.shields.io/badge/CUDA-76B900?style=flat-square&logo=nvidia&logoColor=white)

**Tooling**
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=flat-square&logo=git&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![PowerShell](https://img.shields.io/badge/PowerShell-%235391FE.svg?style=flat-square&logo=powershell&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626.svg?style=flat-square&logo=Jupyter&logoColor=white)
![uv](https://img.shields.io/badge/uv-DE5FE9?style=flat-square&logo=uv&logoColor=white)
![Blender](https://img.shields.io/badge/blender-%23F5792A.svg?style=flat-square&logo=blender&logoColor=white)

---

## 🎨 Outside of engineering

3D modeling in Blender (published on [Sketchfab](https://sketchfab.com/Shouta0108)) and working on my car — which is where the temperature gauge project came from in the first place.

📫 Happy to talk about LiDAR, sensor-based measurement, embedded image processing, or markerless motion capture.
