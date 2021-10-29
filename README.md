[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/rebel-relation-extraction-by-end-to-end/relation-extraction-on-nyt)](https://paperswithcode.com/sota/relation-extraction-on-nyt?p=rebel-relation-extraction-by-end-to-end)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/rebel-relation-extraction-by-end-to-end/relation-extraction-on-conll04)](https://paperswithcode.com/sota/relation-extraction-on-conll04?p=rebel-relation-extraction-by-end-to-end)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/rebel-relation-extraction-by-end-to-end/joint-entity-and-relation-extraction-on-3)](https://paperswithcode.com/sota/joint-entity-and-relation-extraction-on-3?p=rebel-relation-extraction-by-end-to-end)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/rebel-relation-extraction-by-end-to-end/relation-extraction-on-ade-corpus)](https://paperswithcode.com/sota/relation-extraction-on-ade-corpus?p=rebel-relation-extraction-by-end-to-end)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/rebel-relation-extraction-by-end-to-end/relation-extraction-on-re-tacred)](https://paperswithcode.com/sota/relation-extraction-on-re-tacred?p=rebel-relation-extraction-by-end-to-end)
# REBEL: Relation Extraction By End-to-end Language generation

This is the repository for the Findings of EMNLP 2021 paper REBEL: Relation Extraction By End-to-end Language generation. We present a new linearization aproach and a reframing of Relation Extraction as a seq2seq task. The paper can be found [here](docs/EMNLP_2021_REBEL__Camera_Ready_.pdf). If you use the code, please reference this work in your paper:

    @inproceedings{huguet-cabot-navigli-2021-rebel,
    title = "REBEL: Relation Extraction By End-to-end Language generation",
    author = "Huguet Cabot, Pere-Llu{\'\i}s  and
      Navigli, Roberto",
    booktitle = "Findings of the Association for Computational Linguistics: EMNLP 2021",
    month = nov,
    year = "2021",
    address = "Online and in the Barceló Bávaro Convention Centre, Punta Cana, Dominican Republic",
    publisher = "Association for Computational Linguistics",
    url = "https://github.com/Babelscape/rebel/blob/main/docs/EMNLP_2021_REBEL__Camera_Ready_.pdf",
    }


```
Repo structure
| conf  # contains Hydra config files
  | data
  | model
  | train
  root.yaml  # hydra root config file
| data  # data
| datasets  # datasets scripts
| model # model files should be stored here
| src
  | pl_data_modules.py  # LightinigDataModule
  | pl_modules.py  # LightningModule
  | train.py  # main script for training the network
  | test.py  # main script for training the network
| README.md
| requirements.txt
| demo.py # Streamlit demo to try out the model
| setup.sh # environment setup script 
```

## Initialize environment
In order to set up the python interpreter we utilize [conda](https://docs.conda.io/projects/conda/en/latest/index.html)
, the script setup.sh creates a conda environment and install pytorch
and the dependencies in "requirements.txt". 

## REBEL Model and Dataset

Model and Dataset files can be downloaded here:

https://osf.io/4x3r9/?view_only=87e7af84c0564bd1b3eadff23e4b7e54

### CROCODILE: automatiC RelatiOn extraCtiOn Dataset wIth nLi filtEring.

REBEL dataset can be recreated using our RE dataset creator [CROCODILE](https://github.com/Babelscape/crocodile)

## Training and testing

There are conf files to train and test each model. Within the src folder to train for CONLL04 for instance:

    train.py model=rebel_model data=conll04_data train=conll04_train

Once the model is trained, the checkpoint can be evaluated by running:

    test.py model=rebel_model data=conll04_data train=conll04_train do_predict=True checkpoint_path="path_to_checkpoint"

src/model_saving.py can be used to convert a pytorch lightning checkpoint into the hf transformers format for model and tokenizer.


## DEMO

We suggest running the demo to test REBEL. Once the model files are unzipped in the model folder run:

    streamlit run demo.py

And a demo will be available in the browser. It accepts free input as well as data from the sample file in data/rebel/

## Datasets

TACRED is not freely avialable but instructions on how to create Re-TACRED from it can be found [here](https://github.com/gstoica27/Re-TACRED).

For CONLL04 and ADE one can use the script from the [SpERT github](https://github.com/lavis-nlp/spert/blob/master/scripts/fetch_datasets.sh).

For NYT the dataset can be downloaded from [Copy_RE github](https://github.com/xiangrongzeng/copy_re).

Finally the DocRED for RE can be downloaded at the [JEREX github](https://github.com/lavis-nlp/jerex/blob/main/scripts/fetch_datasets.sh)
