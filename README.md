# 🐳 circadiaBase_Docker

**A reproducible Docker environment for chronobiology and actigraphy research, built on Python 3.11 + JupyterLab.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Python](https://img.shields.io/badge/Python-3.11-blue)](https://www.python.org/)
[![JupyterLab](https://img.shields.io/badge/JupyterLab-4.5.6-orange)](https://jupyterlab.readthedocs.io/)
[![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white)](https://docs.docker.com/compose/)

---

## 📖 What is circadiaBase_Docker?

`circadiaBase_Docker` is a self-contained research computing environment for the [Circadia Lab](https://github.com/circadia-bio). It packages a fully pinned Python stack — including pyActigraphy, MNE, YASA, and EntropyHub — into a single Docker image that can be spun up with one command, ensuring reproducibility across machines and collaborators.

The environment is designed to support actigraphy data analysis, EEG/sleep staging, circadian rhythm modelling, and entropy-based time series methods.

---

## ✨ Features

- 🔒 **Fully pinned dependencies** — every package version is locked for reproducibility
- 📓 **JupyterLab** — browser-based notebook interface available at `localhost:8889`
- 📡 **pyActigraphy** — actigraphy analysis via the [artvalencio fork](https://github.com/artvalencio/pyActigraphy), including REST-activity metrics, cosinor analysis, and SSA
- 🧠 **MNE + YASA** — EEG processing and automatic sleep staging
- 📊 **Full scientific stack** — numpy, scipy, pandas, matplotlib, scikit-learn, seaborn, statsmodels, plotly
- 🌀 **EntropyHub** — entropy methods for physiological time series
- 🔧 **Configurable image name** — set via `.env` for project-specific builds

---

## 🗂️ Project Structure

```
circadiaBase_Docker/
├── jupyter/
│   ├── Dockerfile          # Pinned Python 3.11 image definition
│   └── requirements.txt    # Human-readable package manifest
├── docker-compose.yml      # Service definition (port 8889 → 8888)
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

Build and start the environment:

```bash
docker-compose up --build
```

On subsequent runs (no changes to the Dockerfile):

```bash
docker-compose up
```

Then open JupyterLab in your browser at:

```
http://localhost:8889
```

No token or password is required.

---

## 📦 Dependencies

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

### pyActigraphy dependencies

| Package | Version |
|---|---|
| joblib | 1.5.3 |
| lmfit | 1.3.4 |
| numba | 0.65.1 |
| pyexcel | 0.7.4 |
| pyexcel-ods3 | 0.6.1 |
| pyexcel-xlsx | 0.6.1 |
| spm1d | 0.4.53 |
| stochastic | 0.7.0 |
| lxml | 6.1.0 |

---

## 👥 Authors

| Role | Name |
|---|---|
| Developer | Lucas França |
| Contributor | Mario Miguel |

---

## 🤝 Related Tools

- 🌙 [**SleepDiaries**](https://github.com/circadia-bio/SleepDiaries) — cross-platform sleep diary app built for research
- 📋 [**sleep-questionnaires**](https://github.com/circadia-bio/sleep-questionnaires) — validated sleep questionnaire instruments (PSQI, ESS, ISI, MEQ, and more)
- 🔬 [**circadia-bio**](https://github.com/circadia-bio) — the Circadia Lab GitHub organisation

---

## 📄 Licence

Released under the [MIT License](./LICENSE).

Copyright © AlgosL, 2024
