# QSM-Cutoff
## Installation

Clone repository
```
git clone --recurse-submodules git@github.com:Superdude11235/QSM-Cutoff-Jonah.git
```
OPTIONAL: Set up a virtual environment for python3.12 (may be necessary if using WSL)

```
# 1. Update package lists
sudo apt-get update

# 2. Install Python 3.12, venv module, and development headers
sudo apt-get install python3.12 python3.12-venv python3.12-dev

# 3. Create a new virtual environment using Python 3.12
python3.12 -m venv .venv

# 4. Activate the virtual environment
source .venv/bin/activate

# 5. (Optional) Verify Python version and header location
python --version
python -c "from sysconfig import get_paths; print(get_paths()['include'])"
ls $(python -c "from sysconfig import get_paths; print(get_paths()['include'])")/Python.h
```

Set up python environment (recommend python3.12 and above)
```
python3 -m pip install python-sat[aiger,approxmc,cryptosat,pblib]
python3 -m pip install python-sat
python3 -m pip install z3-solver
python3 -m pip install pyyaml
python3 -m pip install pytest
python3 -m pip install setuptools
python3 -m pip install more-itertools
python3 -m pip install itertools
python3 -m pip install numpy
```

Install the PCRE2 development package

```
sudo apt update
sudo apt install libpcre2-dev
```

Install swig
- Install `autotools-dev`, `automake`, `bison`.
```
cd swig-4.2.1
./autogen.sh
./configure
pip install -e .
cd ..
```

Install repycudd
```
cd repycudd
cd cudd-2.4.2
make
make libso
cd ..
```
- Change the python version in repycudd Makefile,Makefile_64bit to your version of python3.1X and add the compilation flag `-I[PATH TO Python.h]`
```
make
export PYTHONPATH=$PYTHONPATH:$(pwd)
```

Install ivy
```
cd ivy
python3 build_submodules.py
sudo python3 setup.py install
sudo python3 setup.py develop
cd ..
```

Install MARCO
```
cd MARCO/src/pyminisolvers
make
make test
cd ../../..
```

## Usage
```=python3
./configure.sh [PATH TO Python.h]
python3 QSM-Cutoff.py [IVY FILE] -s [sort1=size1,sort2=size2 ...]
```
- Run `python3 QSM-Cutoff.py -h` for more information

## Scripts
The directory `scripts` contains the scripts for generating results of our CAV 2025 paper.

## Logs
The directory `CAV_logs` contains experiment logs of our CAV 2025 paper.
