To install the src package locally: pip install -e . 
This project of this project is based off the principles outlined by Patrick Minault in [The Good Research Code Handbook](https://goodresearch.dev)

Saving environment.yaml: conda env export > environment.yml
To update the environment.yaml: conda env update --prefix ./env --file environment.yml --prune
Making new environment from .yaml: conda env create --name recoveredenv --file environment.yml

