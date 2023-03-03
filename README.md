# Islandora workbench Ingest tool
Islandora Workbench is a tool to batch ingests content to Digital Library wbesite using metadata. Each metadata contains data of the child members that called collection, and each collection has it own child pages. These relationships exist in the final metadata that initially added to table using post processing tool, called metadata_process.py (https://github.com/Miladkhanlou/Post-Processing-Tool-For-LDL)

**We can run the workbench on:**
1) Server based website by Bulding Drupal and Islandora an all the dependencies manually. (https://github.com/Miladkhanlou/build-instructions)
2) Islandora sandbox on local host using Docker containers (demo version of islandora). 

## Steps to run workbench on islandora sandbox (demo version of Islandora)
### 1) Install Islandora sandbox on local host (demo version of islandora) 
#### A. clone data from Islandora github page:
`git clone https://github.com/islandora-devops/isle-dc`
#### B. install all the files and dependencies:
`make demo`
#### C. check the passwords for logging into islandora sand box
`cd secrets/live/`
`Nano DRUPAL_DEAFAULT_ACCOUNT_PASSWORD `
	
### 2) Install the islandora Workbench (Migration tool to batch ingest contents using metadata to LDL) 
#### Clone data:
`git clone https://github.com/mjordan/islandora_workbench.git`
`Python3 setup.py install --user`
		
### 3) Configure Islandora Workbench:
#### change location to the `input director` folder and create a configuration YML file.
`cd isle-dc/islandora_workbench/input_data`
`nano LDL_config.yml`
####  Configuration for batch ingest:
		task: create
		host: "https://islandora.traefik.me"
		username: admin
		pasword: password
		input_csv: Presentation/Output.csv
		allow_adding_terms: True
		allow_missing_files: True
***NOTE) The `input_csv` is the name of metadata that workbench will use it to ingest data. it should be located in the `input_data` directory. 
IF you want the metadata to be in the another location, you must specify the location in `input_csv option.***
