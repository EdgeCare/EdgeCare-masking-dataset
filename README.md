# EdgeCare-masking-dataset

## Overview

This repository contains a masking dataset designed for anonymizing personal information in medical text. The dataset consists of structured data where sensitive information is labeled and categorized for easy identification and removal.

## Data Structure

The dataset is stored in [`Dataset.json`](./Dataset.json) and follows the structure below:

```json
{
        "sentence": "The patient, Zoe Reed, has been receiving treatment since 03/12/2020. Contact: +1-555-678-2345.",
        "meta": {
            "note_id": "1750",
            "sl_context": false
        },
        "spans": [
            {
                "id": 0,
                "start": 13,
                "end": 21,
                "label": "PERSON",
                "text": "Zoe Reed"
            },
            {
                "id": 1,
                "start": 58,
                "end": 68,
                "label": "DATE",
                "text": "03/12/2020"
            },
            {
                "id": 2,
                "start": 79,
                "end": 94,
                "label": "PHONE",
                "text": "+1-555-678-2345"
            }
        ]
    }
```

### Fields:
- **sentence**: The original text containing sensitive medical information.
- **meta**: Metadata related to the text sample.
  - **note_id**: Unique identifier for the note.
  - **sl_context**: Boolean flag indicating if the note includes Sri Lankan context.
- **spans**: A list of entities detected in the sentence.
  - **id**: Unique identifier for the entity.
  - **start**: Start index of the entity in the sentence.
  - **end**: End index of the entity in the sentence.
  - **label**: Type of sensitive information.

## Labels

The dataset includes the following entity labels:

| ID  | Label      | Description                                     |
|-----|-----------|-------------------------------------------------|
| 0   | O         | Non-entity tokens                               |
| 1   | PATIENT   | Patient's name                                  |
| 2   | STAFF     | Medical staff name                              |
| 3   | AGE       | Patient's age                                   |
| 4   | BIRTHDATE | Patient's birthdate                             |
| 5   | DATE      | Any date (admission, discharge, etc.)           |
| 6   | PHONE     | Phone number                                    |
| 7   | ID        | Identifiers (e.g. patient ID)             |
| 8   | EMAIL     | Email addresses                                 |
| 9   | LOC       | Location (city, state, address, etc.)           |
| 10  | HOSP      | Hospital or medical institution                 |
| 11  | ORG       | Organizations or institutions                   |
| 12  | URL       | URLs                  |
| 13  | TIMESTAMPS       | Relative dates (e.g. last summer, yesterday)                  |


## Applications

This dataset can be used for:
- **De-identification tasks**: Removing personal identifiers from medical text.
- **Named Entity Recognition (NER) models**: Training machine learning models to detect sensitive information.
- **Privacy-preserving data processing**: Ensuring compliance with HIPAA and other privacy regulations.

## Contributing

If you would like to contribute to this dataset, feel free to:
- Open an issue for any errors or improvements.
- Submit a pull request with additional data or enhancements.
