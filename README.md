# Design of an Intrusion Detection System for Advanced Persistent Threats based on Machine Learning techniques
Alberto Martín Granda

GITST - ETSI Telecomunicación - UPM
	
This repository includes the dataset and code of the different modules developed in the project.

## Requirements

* Suricata
* Python3
* Pandas
* Numpy
* SciKit-learn
* Keras

## Installation

### Detection and Correlation modules Environment

It’s assumed that you run a recent Ubuntu release as the official PPA can be used for the installation.

Pyrhon3 Installation
```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3
```

Suricata Installation
```
sudo add-apt-repository ppa:oisf/suricata-stable
sudo apt update
sudo apt install suricata jq
```

## Repository Structure

### Detection and Correlation Modules

* detect.py: Python script to use the Detection Module
* correlate.py Python script to use the Correlation Module
* clean.py Python script to remove the unnecessary logs

#### DM

Contains the 10 detection modules divided by the 7 APT attack stages

Each modules contains the rule file and a parse.py script necessary for parsing the log files

#### CM

Contains the Alert Filtering module with the filter.py script that filters the csv with the alerts from the Results folder

Contains the Alert Clustering module with the cluster.py script that assigns the alerts output from the Alert Filtering Module a cluster id 

### Data

This folder contains the csv file used as the dataset.

### Machine Learning Module

Jupyter Notebook that carries out the Dataset Pre-processing and the creation and testing of the ML models

Jupyter Notebook is an open-source web application that allows you to create and share documents that contain live code.

## Execution

### Detection Module

Run the following commands in the Detection and Correlation Modules folder:


```
> python3 detect [input pcap file]
> python3 clean
```

A csv file with the same as the pcap file with the output alerts will be stored in the Results folder

### Correlation Module


Run the following command in the Detection and Correlation Modules folder:

```
> python3 correlate
```
This command will merge all the csv files of the Results folder, filter and cluster the alerts resulting in the CM/AC/clustered.csv file that can be used as a dataset for the Machine Learning Module

### Machine Learning Module

Open the Machine Learning Module.ipynb Jupyter Notebook and run the Pre-proccesing section
Run the section corresponding to the ML model you want to generate and test
