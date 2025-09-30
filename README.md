# TIGL
Tranquility Index Glarus

This repository contains all scripts and workflow documentation to reproduce the computation of a spatially explicit Tranquility Index for the Canton of Glarus, Switzerland.

Note on Data Access:
The workflow relies on several datasets  that are not publicly available for redistribution. Therefore, this repository does not include raw data. Instead, we provide a detailed list of required datasets and preprocessing instructions so that users with the appropriate data licenses can reproduce the workflow.

tranquility_glarus/
├── README.md                 # Project description and instructions
├── TIGL.Rmd                  # Single master R script for full workflow
├── documentation/            # Supporting docs (methodology, references)
│   ├── methodology.pdf
│   └── references.bib
├── outputs/                  # (empty) folder structure for generated results
└── data/                     # (empty) folder structure with placeholders only
├── boundaries/           # Study area boundary and buffers
├── tlm/                  # SwissTLM3D & TLMRegio datasets
├── air_pollution/        # NO2, PM10, PM2.5, Ozone rasters
├── bird_species/         # Swiss Bird Atlas
├── noise/                # Road, rail, aviation noise
├── light_emission/       # LABES dataset
├── smell/                # Agricultural + features from TLM
├── presence_people/      # Flickr API derived data
├── remoteness/           # LABES accessibility dataset
├── arealstatistik/       # Arealstatistik
└── VM/                   # VisibilityMap©


Data Requirements

The following datasets must be obtained:
	•	Boundaries: SwissBOUNDARIES3D (swisstopo)
	•	Topographic Data: SwissTLM3D & TLMRegio (swisstopo)
	•	Air Pollution: NO₂, PM₁₀, PM₂.₅, O₃ rasters (BAFU)
	•	Noise: Road and rail noise (BAFU); aviation noise via SIL perimeter (Mollis)
	•	Light Emission: LABES dataset (BAFU)
	•	Remoteness: LABES travel-time dataset (BAFU)
	•	Biodiversity: Swiss Bird Atlas (Vogelwarte)
	•	Land Cover: Arealstatistik (swisstopo)
	•	Human Presence: Flickr API (geotagged images; must be collected by user)

For reproducibility, the repository provides placeholders and directory structure under /data/.
After obtaining the datasets, place them in the respective subfolders following the provided structure.