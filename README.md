

# Download TCGA-LUAD dataset
**Refer to https://www.youtube.com/watch?v=YJxcsm4aJXI**

**Refer to https://github.com/vappiah/DataMiner**

## Create manifest.txt file

Open from a browser the url: https://portal.gdc.cancer.gov/

Select Repository tab
From Files tab Select the follwing:
    Data Category -> trsnscriptome profiling
    Data Type -> Gene Expression Quantification
    Experimental Stratgy -> RNA-Seq
    Workflow Type -> STAR-Counts
From Cases tab select:
    Project -> TCGA-LUAD

Click on AddAllFilesToCart (...600 files will be added) 
Click on Manifest to download the manifest txt file
Rename it to 'manifest.txt' and move it into DataMiner folder

## Download files


**Open in Spyder the tcga_downloader.py**

*I've some modifications as the TCGA api has recently been modified*

**Run the following commands in the Spyder console:**
`from tcga_downloader import *`

`ids=get_ids('manifest.txt')`

`payload=prepare_payload(ids, data_type='Gene Expression Quantification')`

**Run the following command from a command prompt**
`curl --request POST --header "Content-Type: application/json" --data @Payload https://api.gdc.cancer.gov/files > Metadata.tsv`

**Run the following command from Spyder console**
`download_data('Metadata.tsv',sep='\t', outdir='tcga_data')`


## Data Preprocessing

1. Create a folder called `pruned_tcga_data` and then the following subfolders: `Primary Tumor`, `Recurrent Tumor`, and `Solid Tissue Normal`.

2. Run prune_data.py

3. Run prepare_data.py

4. Run tcga_data_prepare.ipynb

## Model Training

1. Run tcga_training.ipynb

