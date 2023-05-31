# Automatic Selection of Dialectal Features of Pskov Dialects in the Speech of Native Speakers Based on the Data of the Opochetsky District of the Pskov Region and the Zapadnodvinsky District of the Tver Region

B. A. thesis by Ekaterina Zalivina

## Description

In this work we analyze approaches for recognizing and detection dialectal features in the speech of informants who have features of Pskov dialects in their speech. After considering the approaches a  tool was created for obtaining TextGrid and eaf files.

## Models for automatic speech recognition

`corpus_1` - data from villages in the Zapadnodvinsky district of the Tver Region

`corpus_2` - data from villages in the Opochetsky District of the Pskov Region 

- wav2vec2

base model: [bond005/wav2vec2-large-ru-golos-with-lm](https://huggingface.co/bond005/wav2vec2-large-ru-golos-with-lm)

| Training data | Test data | Spellchecker use | Notebook |
| --- | --- | --- | --- |
| 70% corpus_1 | 30% corpus_1 | + | [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Speech%20recognition/wav2vec2/Wav2Vec2_train_zapdvin_from_base.ipynb) |
| 70% corpus_2 | 30% corpus_2 | + | [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Speech%20recognition/wav2vec2/Wav2Vec2_train_opochka_from_base.ipynb) |
| 70% corpus_1, 70% corpus_2 | 30% corpus_1 | + |[here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Speech%20recognition/Wav2Vec2_test_zapdvin_on_opochka_model.ipynb)  |
| 70% corpus_1, 70% corpus_2 | 30% corpus_2 | + |[here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Speech%20recognition/wav2vec2/Wav2Vec2_train_opochka_from_zapdvin.ipynb)  |

- QuartzNet

base model: [QuartzNet on Golos](https://sc.link/ZMv)

| Training data | Test data | Spellchecker use | Notebook |
| --- | --- | --- | --- |
| 70% corpus_1 | 30% corpus_1 | + | [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Speech%20recognition/QuartzNet/Quartznet_train_zapdvin_from_base.ipynb) |
| 70% corpus_2 | 30% corpus_2 | + | [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Speech%20recognition/QuartzNet/Quartznet_train_opochka_from_base.ipynb) |
| 70% corpus_1, 70% corpus_2 | 30% corpus_1 | + | [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Speech%20recognition/QuartzNet_Conformer_Transducer_test_zapdvin_from_opochka.ipynb) |
| 70% corpus_1, 70% corpus_2 | 30% corpus_2 | + | [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Speech%20recognition/QuartzNet/Quartznet_train_opochka_from_shetnevo.ipynb) |

- Conformer-Transducer

base model: [stt_ru_conformer_transducer_large](https://catalog.ngc.nvidia.com/orgs/nvidia/teams/nemo/models/stt_ru_conformer_transducer_large)

| Training data | Test data | Spellchecker use | Notebook |
| --- | --- | --- | --- |
| 70% corpus_1 | 30% corpus_1 | - | [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Speech%20recognition/Conformer-Transducer/Conformer_Transducer_train_zapdvin_from_base.ipynb) |
| 70% corpus_2 | 30% corpus_2 | - | [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Speech%20recognition/Conformer-Transducer/Conformer_Transducer_train_opochka_from_base.ipynb) |
| 70% corpus_1, 70% corpus_2 | 30% corpus_1 | - | [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Speech%20recognition/QuartzNet_Conformer_Transducer_test_zapdvin_from_opochka.ipynb) |
| 70% corpus_1, 70% corpus_2 | 30% corpus_2 | - | [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Speech%20recognition/Conformer-Transducer/Conformer_Transducer_train_opochka_from_zapdvin.ipynb) |

## Approaches for dialect features detection

- rule-based
    - data from villages in the Zapadnodvinsky district of the Tver Region - [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Features%20detection/Rule-based/Rule-based_zapdvin.ipynb)
    - data from villages in the Opochetsky District of the Pskov Region - [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Features%20detection/Rule-based/Rule-based_opochka.ipynb)

- binary classification with MFCC
    - data from villages in the Zapadnodvinsky district of the Tver Region - [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Features%20detection/MFCC/MFCC_train_zapdvin.ipynb)
    - data from villages in the Opochetsky District of the Pskov Region - [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Features%20detection/MFCC/MFCC_train_opochka.ipynb)

- XLM-RoBERTa
    - detection any dialect feature (tag DIAL)
        - data from villages in the Zapadnodvinsky district of the Tver Region - [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Features%20detection/Entity%20recognition/ER_train_zapdvin_from_base_DIAL.ipynb)
        - data from villages in the Opochetsky District of the Pskov Region - [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Features%20detection/Entity%20recognition/ER_train_opochka_from_zapdvin_DIAL.ipynb)
    - detection dialect features depending on the language level (tags PHON, MORPH, LEX, SYNT)
        - data from villages in the Zapadnodvinsky district of the Tver Region - [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Features%20detection/Entity%20recognition/ER_train_zapdvin_from_base_all_tags.ipynb)
        - data from villages in the Opochetsky District of the Pskov Region - [here](https://github.com/ustera/dialect-speech-recognition-and-feature-detection/blob/main/Experiments/Features%20detection/Entity%20recognition/ER_train_opochka_from_zapdvin_all_tags.ipynb)

## Usage

Best models Conformer-Transducer and XLM-RoBERTa for data from villages in the Zapadnodvinsky district of the Tver Region and data from villages in the Opochetsky District of the Pskov Region are in Yandex Cloud storage. 

You can download them from the following links:

| model | data | link |
| --- | --- | --- |
| Conformer-Transducer  | Zapadnodvinsky district of the Tver Region | [here](https://storage.yandexcloud.net/dialect-speech-recognition-and-feature-detection/finetuned_conformer.nemo?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=YCAJEUEYBLmE9j6wqGUjKoE1r%2F20230529%2Fru-central1%2Fs3%2Faws4_request&X-Amz-Date=20230529T152617Z&X-Amz-Expires=1209600&X-Amz-Signature=C45CBC6562D8880D5EFFC05A811DC9BB211938AA3CA890EC8DC690952203128F&X-Amz-SignedHeaders=host) |
| Conformer-Transducer | Opochetsky District of the Pskov Region | [here](https://storage.yandexcloud.net/dialect-speech-recognition-and-feature-detection/finetuned_conformer_opochka.nemo?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=YCAJEUEYBLmE9j6wqGUjKoE1r%2F20230529%2Fru-central1%2Fs3%2Faws4_request&X-Amz-Date=20230529T153308Z&X-Amz-Expires=1209600&X-Amz-Signature=8F163739C6D5923A09B2A6888FD0023D0278AB7D2CF7D6590EDEBA01C7ADAF89&X-Amz-SignedHeaders=host) |
| XLM-RoBERTa  | Zapadnodvinsky district of the Tver Region | [here](https://storage.yandexcloud.net/dialect-speech-recognition-and-feature-detection/xlm_roberta_base_dial.zip?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=YCAJEUEYBLmE9j6wqGUjKoE1r%2F20230529%2Fru-central1%2Fs3%2Faws4_request&X-Amz-Date=20230529T154001Z&X-Amz-Expires=1209600&X-Amz-Signature=5AEB7322B6A853EFB3873968A52FFF7F842D35B63466AFFB5812FC5738B80812&X-Amz-SignedHeaders=host) |
| XLM-RoBERTa  | Opochetsky District of the Pskov Region | [here](https://storage.yandexcloud.net/dialect-speech-recognition-and-feature-detection/xlm_roberta_base_dial_V1_opochka.zip?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=YCAJEUEYBLmE9j6wqGUjKoE1r%2F20230529%2Fru-central1%2Fs3%2Faws4_request&X-Amz-Date=20230529T154207Z&X-Amz-Expires=1209600&X-Amz-Signature=764989EFA172BC6F103823BCAB4EC58F135C12B417EDA7357BF46B00F0D34911&X-Amz-SignedHeaders=host) |

All pipeline for transcribing and detecting can be found [here](https://colab.research.google.com/drive/1-L6gwijtLJTVo1TGnX4yttEE3G0mXKNQ?authuser=4#scrollTo=Q8939X9tRNMm).

>You need to change model type (`zapdvin` or `opochka`), path to wav file (variable `url`) in penultimate cell if needed and Run All Cells. You will get file with TextGrid and eaf extensions to work with them in Praat and ELAN.
