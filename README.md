# Antimicrobial activity prediction against Plasmodium falciparum from public ChEMBL and PubChem data

Bioactivity prediction of growth inhibition in Plasmodium falciparum, trained as binary (active/inactive) classifiers from publicly available data in ChEMBL and PubChem. Independent models are trained on multiple bioactivity datasets, corresponding to single-point (percent inhibition) and dose-response (MIC) assays, among others. A ranking score is provided for each model alongside a combined consensus score.

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
- **Output Dimension:** `95`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Plasmodium falciparum from 94 ChEMBL- and PubChem-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 94 sub-models. Recommended threshold: 0.953. |
| individual_inhibition_a | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL4888485 (inhibition %; cutoff 50%; n=147429). Recommended threshold: 0.801. |
| individual_inhibition_b | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL4513220 (inhibition %; cutoff 50%; n=64767). Recommended threshold: 0.824. |
| individual_percenteffect | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL4649945 (percent effect; cutoff 50%; n=33697). Recommended threshold: 0.859. |
| individual_inhibition_c | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL1054501 (inhibition %; cutoff 75%; n=13368). Recommended threshold: 0.521. |
| individual_inhibition_decoys | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL1054500 (inhibition %; cutoff 50%; n=134540). Recommended threshold: 0.85. |
| individual_ec50_decoys_l | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL1040691 (EC50 measurements; cutoff 10 uM; n=41760). Recommended threshold: 0.816. |
| individual_ec50_decoys_k | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL730080 (EC50 measurements; cutoff 10 uM; n=9820). Recommended threshold: 0.834. |
| individual_ic50_decoys_f | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL4888490 (IC50 measurements; cutoff 10 uM; n=5320). Recommended threshold: 0.754. |
| individual_ic50_decoys_c | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL4649964 (IC50 measurements; cutoff 10 uM; n=4330). Recommended threshold: 0.778. |

_10 of 95 columns are shown_
### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`
- **DockerHub**: [https://hub.docker.com/r/ersiliaos/eos4an7](https://hub.docker.com/r/ersiliaos/eos4an7)
- **Docker Architecture:** `AMD64`, `ARM64`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos4an7.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos4an7.zip)

### Resource Consumption
- **Model Size (Mb):** `3654`
- **Environment Size (Mb):** `1896`
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
