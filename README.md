## Prepare  
In order to run this tutorial a working installation of [conda](https://docs.conda.io/en/latest/) is needed. Once you have this, follow the instructions to setup the environm  
ent.  
  
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

  ### Run on a remote Server
  If you plan to run the notebooks from a remote server (e.g. on Tier3) you need to do the following:
  
  Remote:
  ```bash
$ jupyter lab --no-browser --port=XXXX
``` 
Local:
```bash
$ ssh -Y -N -f -L localhost:YYYY:localhost:XXXX remote_username@remote_address
```
From the local browser you can then open the notebook by connecting to ```localhost:YYYY/lab```.

It is also possible to visualize the Dask dashboard for a cluster running remotely. 
Assuming you run a a command like the following:
```python
client = Client(cluster)
```
you can simply type ```client``` in an empty cell to get the main information. Among these, you will see something like the following:

**Dashboard:** [http://A.B.C.D:ZZZZ/status](http://192.33.123.23:8787/status)

ZZZZ is the remote port where the Dashboard is running. From your local machine, you then need to run:
```bash
$ ssh -Y -N -f -L localhost:VVVV:remote_address:ZZZZ remote_user@reomte_address
```
From the local browser you can then open the dashboard by connecting to ```localhost:VVVV/status```.
  
### Content  
* ```1_dask_basics.ipynb```: setup a ```LocalCluster``` and run trivial Python functions in parallel, exploiting both multiprocessing and multithreading;  
* ```2_rdf_basics.ipynb```: use ```ROOT::RDataFrame``` to extract histograms from the ```TTree``` ```Data_13TeV_All``` stored inside ```data/tnp1.root```; use ```EnableImpli  
citMT``` to fully exploit the hardware and speedup the operation;  
* ```3_dask_rdf_local.ipynb```: combine Dask and RDataFrame to get results locally (more details inside);  
* ```4_dask_rdf_cluster.ipynb```: combine Dask and RDataFrame to get results on a SLURM cluster (more details inside).
