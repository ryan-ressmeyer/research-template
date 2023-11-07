This project of this project is based off the principles outlined by Patrick Minault in [The Good Research Code Handbook](https://goodresearch.dev)

### First time setup:

Make a new conda environment from .yaml: `conda env create --name "recoveredenv" --file environment.yml`

Install the src package locally: `pip install -e . `

Pull submodules: `git submodule update --init --recursive`

### Other Notes:

Saving environment.yaml: `conda env export > environment.yml`

To update the environment.yaml: `conda env update --prefix ./env --file environment.yml --prune`

To pull most recent version of submodules: `git submodule update --recursive --remote`