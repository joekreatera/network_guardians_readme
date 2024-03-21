# Guardians of the Network: A Comparative Study of Systems and Datasets for Network Flow Intrusion Detection


## Introduction
This repository shows the different methods and provides the specific datasets used on "Guardians of the Network: A Comparative Study of Systems and Datasets for Network Flow Intrusion Detection" paper. By using this repo, researchers can jump start on comparing Network Intrusion Detection Systems using the protocols presented on  the study.

## Paper Abstract
Intelligent Intrusion Detection Systems are being developed to analyze and detect anomalous traffic since cyberattacks are growing and transforming each month globally. Network flows, an aggregated version of communications between devices, are studied to classify the specific attacks as different policies are needed to protect the devices and infrastructure. To train these systems, researchers use synthetic labeled datasets, or operational networks identified traffic that represents updated and common threats. As threats represent a fast-evolving environment, benchmarks are continuously developed, and solutions must be thoroughly tested, missing a more comprehensive characterization of advantages and opportunities. In this work, we study 7 different methods on 14 updated benchmarks analyzing the implementation details. A comparison using the Macro F1 score performance indicator highlights each solution’s operation regarding different scenarios. Finally, a discussion on the characteristics of the methods and benchmarks focuses on usage options for practitioners and researchers.

## Datasets

The study covers 14 datasets in different formats and files. The following links contain a final pickle format file already joined and cleaned up (when necessary). Pickle format is a serialization format used by Python to write and transport binary objects. By reading these files, developers and researchers avoid large loading times. To read one of these files, the process is simple:

```
import pickle
with open('opcua_no_id_complete.pkl','rb') as f:
    df = pickle.load(f)
    print( df.info() )
```

All datasets are Pandas DataFrames. 

### Files:
Each complete dataset is provided. The smallest is 11 MB and the largest is 17 GB aprox. A complete download of the 14 datasets would need 47 GB. These datasets have already been processed to the smallest data type possible on each column. 

Four options are provided. The FULL version of the dataset is a pandas dataframe with the data preprocessed from the original. The TRAINING dataset is a 70% subset while VALIDATION and TESTING are a 15% split respectively. Some methods did not need VALIDATION. When this happened, TRAINING and VALIDATION were merged.


| DB           | Size (GB)    | FULL     | TRAINING | VALIDATION | TESTING  |
|--------------|--------------|----------|----------|------------|----------|
| Opcua        | 0.011        | Download | Download | Download   | Download |
| InSDN        | 0.083        | Download | Download | Download   | Download |
| NDSec-1      | 0.136        | Download | Download | Download   | Download |
| Hikari       | 0.165        | Download | Download | Download   | Download |
| UNSW NB15    | 0.303        | Download | Download | Download   | Download |
| CIC IDS 2017* | 0.553        | Download | Download | Download   | Download |
| CIDDS        | 0.672        | Download | Download | Download   | Download |
| ISCX 2012    | 0.990        | Download | Download | Download   | Download |
| ToN IoT      | 2.080        | Download | Download | Download   | Download |
| USB IDS      | 2.530        | Download | Download | Download   | Download |
| Litnet       | 4.260        | Download | Download | Download   | Download |
| BotIot       | 4.630        | Download | Download | Download   | Download |
| DDoS 2019    | 13.50        | Download | Download | Download   | Download |
| CSE CIC 2018* | 17.00        | Download | Download | Download   | Download |

* The original versions had bugs after Network Flows extraction. These versions come from fixed versions. 

## Methods

All the techniques implemented are provided by their original authors. In the following table, the original link is provided as well as a working copy that was used on the experiments. The names follow the convention shown on the paper. Each copy has a job-scripts folder with different shell scripts that were used for the SLURM jobs. The files should be used as an example of how to run each algorithm. All of these methods suppose, regarding the job scripts, that data is located two levels above, inside "datasets/<dataset name>" folder. Methods worked with Python versions 9,10 and 11, as each job script shows.   



| Method       | Working Copy                                                                   | Original version                                                      |
|--------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------|
| LCCDE        | [Github](https://github.com/joekreatera/cc_boost_ids_ml)                       | [Github](https://github.com/Western-OC2-Lab/Intrusion-Detection-System-Using-Machine-Learning)              |
| EFC          | [Github](https://github.com/joekreatera/cc_efc_ids_ml)                         | [Github](https://github.com/EnergyBasedFlowClassifier/EFC-package)              |
| NN           | [Github](https://github.com/joekreatera/cc_deep_learning_ids_tf)               | [Github](https://github.com/Colorado-Mesa-University-Cybersecurity/DeepLearning-IDS)              |
| CNN          | [Github](https://github.com/joekreatera/cc_deep_learn_ids_tf)                  | [Github](https://github.com/dwday/deep_learn_ids)              |
| DBN          | [Github](https://github.com/joekreatera/cc_dbn_ids_torch)                      | [Github](https://github.com/othmbela/dbn-based-nids)              |
| EGS          | [Github](https://github.com/joekreatera/cc_e_graph_sage_ids_torch)             | [Github](https://github.com/waimorris/E-GraphSAGE)              |
| CFC          | [Github](https://github.com/joekreatera/cc_conflow_ids_torch)                  | [Github](https://github.com/AshinWang/ConFlow?tab=readme-ov-file)              |


### Libraries

All the solutions presented above had different configurations. It is recommended to use virtual environments as some of them were based on PyTorch while on Keras with Tensorflow or even XBoost. 
