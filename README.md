# Antimicrobial activity prediction against Plasmodium falciparum from public ChEMBL and PubChem data

Bioactivity prediction of growth inhibition in Plasmodium falciparum, trained as binary (active/inactive) classifiers from publicly available data in ChEMBL and PubChem. Independent models are trained on multiple bioactivity datasets, corresponding to single-point (Inhibition) and dose-response (MIC) assays, among others. A ranking score is provided for each model alongside a combined consensus score.

This model was incorporated on 2026-05-19.Last packaged on 2026-06-02.

## Information
### Identifiers
- **Ersilia Identifier:** `eos4an7`
- **Slug:** `antimicrobial-activity-pfalciparum`

### Domain
- **Task:** `Annotation`
- **Subtask:** `Activity prediction`
- **Biomedical Area:** `Malaria`
- **Target Organism:** `Plasmodium falciparum`
- **Tags:** `Protozoa`, `Antiparasitic activity`, `Antimicrobial activity`, `ChEMBL`

### Input
- **Input:** `Compound`
- **Input Dimension:** `1`

### Output
- **Output Dimension:** `52`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Plasmodium falciparum from 51 ChEMBL- and PubChem-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 51 sub-models. Recommended threshold: 0.639. |
| chembl_single_point_0 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 19 assays (147560 compounds). Recommended threshold: 0.852. |
| chembl_single_point_1 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 13 assays (55965 compounds). Recommended threshold: 0.844. |
| chembl_single_point_2 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 20 assays (33900 compounds). Recommended threshold: 0.848. |
| chembl_single_point_3 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 21 assays (20662 compounds). Recommended threshold: 0.978. |
| chembl_single_point_4 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 16 assays (15912 compounds; incl. 2438 added negatives). Recommended threshold: 0.479. |
| chembl_single_point_5 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 20 assays (603 compounds). Recommended threshold: 0.648. |
| chembl_single_point_6 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 16 assays (250 compounds; incl. 6 added negatives). Recommended threshold: 0.433. |
| chembl_dose_response_00 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 173 assays (29588 compounds; incl. 14148 added negatives). Recommended threshold: 0.526. |
| chembl_dose_response_01 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 869 assays (13456 compounds; incl. 3418 added negatives). Recommended threshold: 0.513. |

_10 of 52 columns are shown_
### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`
- **DockerHub**: [https://hub.docker.com/r/ersiliaos/eos4an7](https://hub.docker.com/r/ersiliaos/eos4an7)
- **Docker Architecture:** `AMD64`, `ARM64`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos4an7.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos4an7.zip)

### Resource Consumption
- **Model Size (Mb):** `2478`
- **Environment Size (Mb):** `7208`
- **Image Size (Mb):** `7875.88`

**Computational Performance (seconds):**
- 10 inputs: `132.59`
- 100 inputs: `392.86`
- 10000 inputs: `-1`

### References
- **Source Code**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication Type:** `Other`
- **Publication Year:** `2026`
- **Ersilia Contributor:** [arnaucoma24](https://github.com/arnaucoma24)

### License
This package is licensed under a [GPL-3.0](https://github.com/ersilia-os/ersilia/blob/master/LICENSE) license. The model contained within this package is licensed under a [GPL-3.0-or-later](LICENSE) license.

**Notice**: Ersilia grants access to models _as is_, directly from the original authors, please refer to the original code repository and/or publication if you use the model in your research.


## Use
To use this model locally, you need to have the [Ersilia CLI](https://github.com/ersilia-os/ersilia) installed.
The model can be **fetched** using the following command:
```bash
# fetch model from the Ersilia Model Hub
ersilia fetch eos4an7
```
Then, you can **serve**, **run** and **close** the model as follows:
```bash
# serve the model
ersilia serve eos4an7
# generate an example file
ersilia example -n 3 -f my_input.csv
# run the model
ersilia run -i my_input.csv -o my_output.csv
# close the model
ersilia close
```

## About Ersilia
The [Ersilia Open Source Initiative](https://ersilia.io) is a tech non-profit organization fueling sustainable research in the Global South.
Please [cite](https://github.com/ersilia-os/ersilia/blob/master/CITATION.cff) the Ersilia Model Hub if you've found this model to be useful. Always [let us know](https://github.com/ersilia-os/ersilia/issues) if you experience any issues while trying to run it.
If you want to contribute to our mission, consider [donating](https://www.ersilia.io/donate) to Ersilia!
