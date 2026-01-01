# Asbab al-Nuzul Dataset <!-- omit in toc -->

## Contents
- [Introduction](#introduction)
- [Data Source](#data-source)
- [Dataset Structure](#dataset-structure)
  - [Plaintext (`data/plaintext/`)](#plaintext-dataplaintext)
  - [JSON (`data/structured/json/`)](#json-datastructuredjson)
  - [CSV (`data/structured/csv/`)](#csv-datastructuredcsv)
- [Data Transformation](#data-transformation)
- [Contributing](#contributing)

# Introduction 

**Asbab al-Nuzul** (أسباب النزول, "Occasions of Revelation") refers to the historical context and circumstances surrounding the revelation of specific Quranic verses. Understanding these occasions is crucial for:

- Proper interpretation of Quranic verses
- Understanding the historical context of revelation
- Resolving apparent contradictions

[Wikipedia Article](https://en.wikipedia.org/wiki/Asbab_al-Nuzul)


# Data Source

This dataset is based on the book:

**صحيح أسباب النزول دراسة حديثية**  
*Author: إبراهيم محمد العلي (Ibrahim Muhammad al-Ali)*

The book provides the most authentic occasions of revelation with hadith analysis.

**Book Link:** [https://quranpedia.net/book/25685](https://quranpedia.net/book/25685)

# Dataset Structure

The dataset is available in three formats:

## Plaintext (`data/plaintext/`)

```
plaintext/
├── 002/            # Surah number (e.g., Al-Baqarah)
│   ├── 089/        # Ayah number
│   │   ├── 1.md    # First occasion text
│   │   └── 2.md    # Second occasion text (if multiple)
│   ├── 097/
│   └── ...
├── 003/
└── ...
```

- Organized by Surah number (zero-padded to 3 digits)
- Each Surah contains folders for Ayah numbers (or ranges like `200-201-202`)
- Each Ayah folder contains one or more text files with occasion descriptions
- All text files are UTF-8 encoded

## JSON (`data/structured/json/`)

```
json/
├── 002.json    # Individual Surah files
├── 003.json
├── ...
└── all.json    # Complete dataset
```

**Structure per Surah:**
```json
[
  {
    "surah": 2,
    "ayahs": [89, 90],
    "occasions": [
      "Occasion text in Arabic...",
      "Another occasion if multiple exist..."
    ]
  }
]
```

**Fields:**
- `surah`: Surah number (integer)
- `ayahs`: Array of ayah numbers covered by this occasion
- `occasions`: Array of occasion descriptions (strings)

## CSV (`data/structured/csv/`)

```
csv/
├── 002.csv     # Individual Surah files
├── 003.csv
├── ...
└── all.csv     # Complete dataset
```

**Structure:**
```csv
surah,ayahs,occasion
2,"89-90","Occasion text in Arabic..."
2,"89-90","Another occasion for ayahs 89-90..."
```

**Columns:**
- `surah`: Surah number
- `ayahs`: Ayah number or range (e.g., "89" or "89-90-91")
- `occasion`: Occasion description text

**Note:** CSV files use UTF-8 with BOM encoding for Excel compatibility on Windows.

# Data Transformation

The `scripts/python/transform.ipynb` Jupyter notebook processes the plaintext data and generates JSON and CSV formats. You can:

1. Modify the notebook to create custom data formats
2. Add additional processing or filtering
3. Generate formats specific to your use case

**Requirements:**
```bash
pip install -r scripts/python/requirements.txt
```
# Contributing

If you find any issues, errors in the text, or mistakes in transcription, please feel free to open an issue or contact me. Contributions and corrections are highly appreciated!
