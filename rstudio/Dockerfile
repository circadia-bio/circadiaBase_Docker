FROM rocker/rstudio:4.4

# Install tidyverse + verse stack using rocker's own scripts
RUN /rocker_scripts/install_tidyverse.sh
RUN /rocker_scripts/install_verse.sh

# System dependencies for R packages
RUN apt-get update && apt-get install -y --no-install-recommends \
    libglpk-dev \
    libgmp-dev \
    libxml2-dev \
    libcurl4-openssl-dev \
    libssl-dev \
    libfontconfig1-dev \
    libharfbuzz-dev \
    libfribidi-dev \
    libfreetype6-dev \
    libpng-dev \
    libtiff5-dev \
    libjpeg-dev \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# ggplot2 extensions
RUN Rscript -e "install.packages(c( \
    'ggpubr', \
    'ggrepel', \
    'ggridges', \
    'patchwork', \
    'cowplot', \
    'scales', \
    'viridis', \
    'RColorBrewer' \
), repos='https://cloud.r-project.org', Ncpus=4)"

# Stats packages
RUN Rscript -e "install.packages(c( \
    'lme4', \
    'lmerTest', \
    'emmeans', \
    'MuMIn', \
    'effectsize', \
    'performance', \
    'parameters', \
    'see' \
), repos='https://cloud.r-project.org', Ncpus=4)"

# Bayesian stats
RUN Rscript -e "install.packages(c( \
    'brms', \
    'bayesplot', \
    'tidybayes', \
    'rstanarm' \
), repos='https://cloud.r-project.org', Ncpus=4)"

# Sleep & circadian packages
RUN Rscript -e "install.packages(c( \
    'GGIR', \
    'ActCR', \
    'circacompare', \
    'cosinor', \
    'cosinor2' \
), repos='https://cloud.r-project.org', Ncpus=4)"

# lunaR from GitHub (Luna project)
RUN Rscript -e "devtools::install_github('remnrem/luna')"
