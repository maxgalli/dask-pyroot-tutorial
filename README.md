## Prepare
In order to run this tutorial a working installation of [conda](https://docs.conda.io/en/latest/) is needed. Once you have this, follow the instructions to setup the environment.

### 1. Clone this repository
```bash
$ git clone https://github.com/maxgalli/dask-pyroot-tutorial
$ cd dask-pyroot-tutorial
```

### 2. Create a conda environment
```bash
$ conda env create -f environment.yml
```

## Run
The suggested way to execute the notebooks is from inside a **JupyterLab** environment, which is installed with the previous commands.
```bash
$ cd dask-pyroot-tutorial
$ jupyter lab
```

The notebooks are meant to be read and executed in order (1-4). Unfortunately, number 4 can be run *as it is* only on at Tier3-PSI, which runs a SLURM job queuing system.
### Content
* ```1_dask_basics.ipynb```:  setup a ```LocalCluster``` and run trivial Python functions in parallel, exploiting both multiprocessing and multithreading;
* ```2_rdf_basics.ipynb```:  use ```ROOT::RDataFrame``` to extract histograms from the ```TTree``` ```Data_13TeV_All``` stored inside ```data/tnp1.root```; use ```EnableImplicitMT``` to fully exploit the hardware and speedup the operation;
* ```3_dask_rdf_local.ipynb```: combine Dask and RDataFrame to get results locally (more details inside);
* ```4_dask_rdf_cluster.ipynb```: combine Dask and RDataFrame to get results on a SLURM cluster (more details inside).
