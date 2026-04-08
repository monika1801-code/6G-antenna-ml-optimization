# Design and Optimization of a Terahertz Antenna for 6G Applications using CSRR and Machine Learning

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-0A66C2?style=for-the-badge)
![HFSS](https://img.shields.io/badge/Ansys%20HFSS-FFB71B?style=for-the-badge)
![6G Research](https://img.shields.io/badge/6G-Research-purple?style=for-the-badge)

> **Published Research Project**  
> This repository contains the implementation, simulation outputs, datasets, and machine learning workflow behind our research work:  
> **"Design and Optimization of a Terahertz Antenna for 6G Applications using CSRR and Machine Learning"**  
> **Authors:** K. Rojamani, R.S. Monika, T.A.K. Chaitanya, K. Prashanth Kumar  
> **Institution:** Krishna University College of Engineering & Technology, Machilipatnam, Andhra Pradesh, India

---

## Project Overview

This project presents a **Terahertz (THz) antenna design for 6G applications** integrated with a **Machine Learning-based optimization workflow** to improve antenna performance and reduce simulation effort.

The antenna was designed and analyzed using **Ansys HFSS**, while simulation outputs were converted into structured datasets for machine learning-based parameter prediction. The work combines:

- **Electromagnetic antenna design**
- **CSRR-based performance enhancement**
- **HFSS simulation analysis**
- **Regression-based machine learning optimization**

The main goal was to optimize critical antenna design parameters more efficiently than traditional trial-and-error simulation.

---

## Problem Statement

Designing a THz antenna for 6G communication requires careful tuning of physical parameters. One of the most sensitive design parameters in this work was the **patch width (W1)**.

### Traditional optimization process:
1. Manually change W1
2. Re-simulate the antenna in HFSS
3. Evaluate **S11 (Return Loss)** and **VSWR**
4. Repeat until acceptable performance is obtained

This process is:
- time-consuming
- computationally expensive
- dependent on manual trial-and-error

To address this, this project uses **Machine Learning to predict the optimal antenna parameter directly from simulation data**, reducing repeated HFSS iterations.

---

## Research Contribution

This work demonstrates how **Machine Learning can assist antenna optimization** by learning from simulation data and identifying better-performing design parameters.

Instead of relying only on repeated electromagnetic simulations, the project introduces a **data-driven optimization pipeline** for THz antenna design.

---

## Key Results

| Metric | Initial Design | After ML Optimization |
|---|---:|---:|
| Patch width (W1) | 4 µm | **36 µm** |
| Return loss (S11) | −39.6 dB @ 3.6–3.8 THz | −32.7 dB @ 1.6–1.7 THz |
| Antenna Gain | 3.52 dB | **6.42 dB** |
| Bandwidth | 3.6–3.8 THz | 1.6–1.7 THz |

## Resume Highlights

- Designed and simulated a **Terahertz antenna for 6G applications** using **Ansys HFSS**
- Applied **Machine Learning regression models** to optimize antenna design parameters
- Built a simulation-driven dataset and evaluated **13 ML models** for antenna parameter prediction
- Identified an optimized antenna configuration that improved **gain from 3.52 dB to 6.42 dB**
- Combined **electromagnetic simulation + data-driven optimization** into a research workflow

### Key Insight
The **machine learning model identified an optimized patch width** that improved antenna gain significantly and shifted the operating response to a different resonant region.

This shows that ML can serve as an effective **design-assistance tool** for antenna engineers and researchers.

---

## Antenna Design

The antenna is a **concentric circular patch antenna** designed for **terahertz-band operation**, intended for next-generation **6G wireless communication systems**.

A **Complementary Split Ring Resonator (CSRR)** was introduced in the ground plane to improve:
- impedance matching
- resonance behavior
- electromagnetic response characteristics

### Simulation Tool
- **Ansys HFSS (High Frequency Structure Simulator)**

---

## Antenna Parameters

| Parameter | Dimension |
|---|---:|
| Substrate length/width (Ls = Ws) | 100 µm |
| Substrate height (Hs) | 10 µm |
| Ground plane length (Lg) | 100 µm |
| Ground plane width (Wg) | 50 µm |
| Patch outer radius (R1) | 40 µm |
| Patch inner radius (R2) | 30 µm |
| CSRR outer ring (L1 × W1) | 40 × 30 µm |
| CSRR inner ring (L2 × W2) | 30 × 20 µm |
| Feed line (Lf = Wf) | 5 µm |
| Parasitic element (L3 × W3) | 30 × 4 µm |

---

## HFSS Simulation Outputs

The antenna was simulated in HFSS and evaluated using key performance metrics such as:

- **S-Parameters (S11 / Return Loss)**
- **VSWR**
- **Radiation Pattern**
- **3D Polar Plot**
- **Comparative response before and after optimization**

The simulation outputs were then exported and used as the basis for the machine learning workflow.

---

## Machine Learning Approach

The machine learning component of this project was used to predict the antenna parameter **W1 (patch width)** based on simulation characteristics.

### Objective
Use antenna response data to learn the relationship between:
- frequency response
- return loss
- impedance behavior

and then predict the **best-performing antenna configuration**.

---

## Dataset

The dataset was generated by varying the antenna design parameter **W1 from 4 µm to 60 µm** and recording simulation outputs.

### Dataset Features

| Column | Description |
|---|---|
| `Freq_Thz` | Simulation frequency in terahertz |
| `S11-db` | Return loss in dB |
| `VSWR` | Voltage Standing Wave Ratio |
| `W1` | Patch width in µm (target parameter) |

### Dataset Summary
- Total rows: **~1,806**
- Train/Test Split: **80% / 20%**
- Input Features: `Freq_Thz`, `S11-db`
- Target Variable: `W1`

---

## Models Evaluated

A total of **13 regression models** were trained and compared.

| Model | MSE | R² |
|---|---:|---:|
| SVR (Linear Kernel) | 361.54 | −0.062 |
| SVR (Polynomial Kernel) | 359.65 | −0.056 |
| SVR (RBF Kernel) | 352.58 | −0.036 |
| SVR (Tuned via GridSearchCV) | 323.84 | 0.072 |
| Linear Regression | 348.07 | 0.003 |
| ElasticNet | 349.27 | −0.001 |
| Polynomial Regression (degree=1) | 348.07 | 0.003 |
| Random Forest Regressor | 291.12 | 0.166 |
| Gradient Boosting Regressor | 298.58 | 0.145 |
| XGBoost Regressor | 319.25 | 0.086 |
| LightGBM Regressor | 271.53 | 0.222 |
| **CatBoost Regressor** | **248.82** | **0.287** |
| KNN Regressor (k=5) | 338.93 | 0.029 |

### Best Model
✅ **CatBoost Regressor** performed best based on:
- **lowest Mean Squared Error (MSE)**
- **highest R² score**

---

## Hyperparameter Tuning

Support Vector Regression (SVR) was additionally tuned using **GridSearchCV**.

### Parameter Grid

```python
param_grid = {
    'kernel': ['linear', 'rbf', 'poly'],
    'C': [0.1, 1, 10, 100],
    'gamma': ['scale', 'auto', 0.01, 0.1, 1],
    'epsilon': [0.01, 0.1, 0.5, 1]
}
```


## Best Tuned SVR

- kernel='rbf'
- C=10
- epsilon=1
- gamma=1

### Performance:

- MSE: 323.84
- R²: 0.072

Although tuning improved SVR performance, CatBoost still outperformed all other models.

##  Why Machine Learning Helped

This project shows how machine learning can support antenna design by:

- reducing repeated HFSS simulation cycles
- accelerating design-space exploration
- identifying better-performing parameter combinations
- supporting data-driven engineering decisions

This is especially useful in THz antenna research, where small dimensional changes can significantly affect resonant behavior.


##  Repository Structure

``` bash
6G-antenna-ml-optimization/
│
├── Data/                  # CSV datasets from HFSS simulations
├── HFSS_design/           # HFSS output plots and antenna simulation visuals
├── Notebooks/             # Jupyter notebooks for ML model training and analysis
├── README.md
├── requirements.txt
└── .gitignore
```

## How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/monika1801-code/6G-antenna-ml-optimization.git
cd 6G-antenna-ml-optimization
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

Then open the notebooks inside the `Notebooks/` folder and run them in sequence.

## Requirements

- pandas
- numpy
- matplotlib
- scikit-learn
- xgboost
- lightgbm
- catboost
- tensorflow
- jupyter
- notebook

### Install them using:

- pip install -r requirements.txt

## Applications

This project is relevant to:

- 6G antenna research
- Terahertz communication systems
- ML-assisted electromagnetic design
- Simulation-driven optimization
- Intelligent wireless system development

## Future Scope

 Possible extensions of this work include:

 - deep learning models for multi-parameter prediction
 - multi-objective optimization of gain, bandwidth, and return loss
 - optimization of additional antenna geometry parameters
 - fabrication and hardware validation
 - integration with beamforming / massive MIMO-based 6G systems


## Citation

If you use this work in research or reference this repository, please cite:

"Design and Optimization of a Terahertz Antenna for 6G Applications
using CSRR and Machine Learning,"
Krishna University College of Engineering & Technology, 2024.
Authors
K. Rojamani — Assistant Professor, Department of ECE
R.S. Monika — UG Student
T.A.K. Chaitanya — UG Student
K. Prashanth Kumar — UG Student


## Keywords

6G Terahertz Antenna CSRR Machine Learning HFSS CatBoost Antenna Optimization Wireless Communication Regression Modeling
