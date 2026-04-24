# 🐳 circadiaBase_Docker

**A reproducible Docker environment for chronobiology and actigraphy research, built on Python 3.11 + R 4.4.2 + JupyterLab + RStudio.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Python](https://img.shields.io/badge/Python-3.11-blue)](https://www.python.org/)
[![R](https://img.shields.io/badge/R-4.4.2-276DC3?logo=r&logoColor=white)](https://www.r-project.org/)
[![JupyterLab](https://img.shields.io/badge/JupyterLab-4.5.6-orange)](https://jupyterlab.readthedocs.io/)
[![RStudio](https://img.shields.io/badge/RStudio-rocker%2Fverse-75AADB?logo=rstudio&logoColor=white)](https://rocker-project.org/)
[![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white)](https://docs.docker.com/compose/)

---

## 📖 What is circadiaBase_Docker?

`circadiaBase_Docker` is a self-contained research computing environment for the [Circadia Lab](https://github.com/circadia-bio). It packages a fully pinned Python + R stack into two Docker services that share the same volume, ensuring reproducibility across machines and collaborators.

- **JupyterLab** — Python-based actigraphy, EEG/sleep staging, entropy, and circadian modelling
- **RStudio Server** — R-based sleep and circadian analyses with GGIR, ActCR, circacompare, brms, and lme4

---

## ✨ Features

- 🔒 **Fully pinned dependencies** — every package version is locked for reproducibility
- 📓 **JupyterLab** — browser-based notebook interface at `localhost:8889`
- 🧪 **RStudio Server** — full IDE for R at `localhost:8787`
- 📂 **Shared volume** — both services read/write the same project files
- 📡 **pyActigraphy 1.2.2** — actigraphy analysis including REST-activity metrics, cosinor, and SSA
- 🧠 **MNE + YASA** — EEG processing and automatic sleep staging
- 📊 **Full scientific stack** — numpy, scipy, pandas, matplotlib, scikit-learn, seaborn, statsmodels, plotly
- 🌀 **EntropyHub** — entropy methods for physiological time series
- 📈 **R stats** — lme4, lmerTest, brms, emmeans, ggplot2 extensions
- 🕰️ **R circadian** — GGIR, ActCR, circacompare, cosinor, lunaR
- 🔧 **Configurable image name** — set via `.env` for project-specific builds

---

## 🗂️ Project Structure

```
circadiaBase_Docker/
├── jupyter/
│   └── Dockerfile          # Pinned Python 3.10 image definition
├── rstudio/
│   └── Dockerfile          # Rocker/verse R 4.4.2 image definition
├── docker-compose.yml      # Two services: jupyter (8889) + rstudio (8787)
├── .env                    # Local config (IMAGE_NAME) — not committed
├── .env.example            # Template for .env
├── .gitignore
└── LICENSE
```

---

## 🚀 Getting Started

### Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (or Docker Engine + Compose plugin)

### Installation

1. Clone the repository:

```bash
git clone https://github.com/circadia-bio/circadiaBase_Docker.git
cd circadiaBase_Docker
```

2. Create your `.env` file from the example:

```bash
cp .env.example .env
```

3. (Optional) Edit `IMAGE_NAME` in `.env` to match your project, e.g. `IMAGE_NAME=my_project`.

### Running

Build and start both services:

```bash
docker-compose up --build
```

On subsequent runs:

```bash
docker-compose up
```

| Service | URL | Notes |
|---|---|---|
| JupyterLab | http://localhost:8889/lab | No token required |
| RStudio Server | http://localhost:8787 | No password required |

To run only one service:

```bash
docker-compose up jupyter
docker-compose up rstudio
```

---

## 📦 Python Dependencies

### Core environment

| Package | Version | Purpose |
|---|---|---|
| Python | 3.11 | Base interpreter |
| JupyterLab | 4.5.6 | Notebook interface |
| notebook | 7.5.5 | Classic notebook support |

### Scientific stack

| Package | Version | Purpose |
|---|---|---|
| numpy | 1.26.4 | Numerical computing |
| scipy | 1.14.1 | Scientific algorithms |
| pandas | 2.2.2 | Tabular data |
| matplotlib | 3.9.2 | Plotting |
| seaborn | 0.13.2 | Statistical visualisation |
| scikit-learn | 1.5.2 | Machine learning |
| statsmodels | 0.14.6 | Statistical modelling |
| plotly | 4.11.0 | Interactive plots |

### Chronobiology & sleep

| Package | Version | Purpose |
|---|---|---|
| pyActigraphy | GitHub (artvalencio) | Actigraphy analysis, REST-activity, cosinor, SSA |
| mne | 1.8.0 | EEG/MEG processing |
| yasa | 0.6.5 | Automatic sleep staging |
| EntropyHub | 2.0 | Entropy-based time series methods |

---

## 📦 R Dependencies

### Base image

| Package | Version | Purpose |
|---|---|---|
| R | 4.4.2 | Base interpreter |
| rocker/verse | 4.4.2 | tidyverse, devtools, rmarkdown, ggplot2 |

### ggplot2 extensions

`ggpubr`, `ggrepel`, `ggridges`, `patchwork`, `cowplot`, `scales`, `viridis`, `RColorBrewer`

### Stats packages

`lme4`, `lmerTest`, `emmeans`, `MuMIn`, `effectsize`, `performance`, `parameters`, `see`

### Bayesian stats

`brms`, `bayesplot`, `tidybayes`, `rstanarm`

### Sleep & circadian

`GGIR`, `ActCR`, `circacompare`, `cosinor`, `cosinor2`, `lunaR` (GitHub)

---

## 👥 Authors

| Role | Names |
|---|---|
| Principal Investigators | Lucas França, Mario Leocadio-Miguel |
| Development | Lucas França, Mario Leocadio-Miguel |

---

## 🤝 Related Tools

- 🌙 [**SleepDiaries**](https://github.com/circadia-bio/SleepDiaries) — cross-platform sleep diary app built for research
- 📋 [**sleep-questionnaires**](https://github.com/circadia-bio/sleep-questionnaires) — validated sleep questionnaire instruments (PSQI, ESS, ISI, MEQ, and more)
- 🔬 [**circadia-bio**](https://github.com/circadia-bio) — the Circadia Lab GitHub organisation

---

## 📄 Licence

![](https://raw.githubusercontent.com/circadia-bio/circadiaBase_Docker/main/assets/images/logo.png)

Copyright © Circadia Lab — Lucas França & Mario Leocadio-Miguel

Released under the [MIT License](./LICENSE).
