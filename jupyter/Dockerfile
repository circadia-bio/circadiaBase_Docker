FROM python:3.11-slim

# System dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    gcc \
    gfortran \
    git \
    curl \
    libhdf5-dev \
    libffi-dev \
    libssl-dev \
    pkg-config \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Upgrade pip
RUN pip install --upgrade pip

# Install Jupyter
RUN pip install jupyterlab notebook

# Install pinned scientific stack first (order matters for binary compatibility)
RUN pip install \
    numpy==1.26.4 \
    scipy==1.14.1 \
    pandas==2.2.2

# Install remaining requirements
RUN pip install \
    matplotlib==3.9.2 \
    scikit-learn==1.5.2 \
    seaborn==0.13.2 \
    mne==1.8.0 \
    EntropyHub==2.0 \
    yasa==0.6.5 \
    plotly==4.11.0

# Install pyActigraphy dependencies explicitly before the package itself
RUN pip install \
    joblib \
    lmfit \
    numba \
    pyexcel \
    pyexcel-ods3 \
    pyexcel-xlsx \
    spm1d \
    statsmodels \
    stochastic \
    lxml

# Install pyActigraphy from GitHub (artvalencio fork)
RUN pip install git+https://github.com/artvalencio/pyActigraphy

ENV HDF5_USE_FILE_LOCKING=FALSE

WORKDIR /home/jovyan/${IMAGE_NAME}

EXPOSE 8888

CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root", "--NotebookApp.token=''"]
