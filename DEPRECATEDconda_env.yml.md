name: ccmultiomkge
channels:
  - conda-forge
dependencies:
  - python=3.9.*
  - pip
  - r-base=4.*
  - r-tidyverse=1.3.*
  - r-seurat=4.1.*
  - pip:
    - numpy
    - pandas
    - notebook
    - scanpy
    - networkx
    - pykeen
    - scikit-learn
    - torch
    - scprep
    - matplotlib
    - seaborn
    - rpy2
    - anndata2ri
    - biomart
    - magic-impute
