# TIGL
Tranquility Index Glarus

This repository contains all scripts and workflow documentation to reproduce the computation of a spatially explicit Tranquility Index for the Canton of Glarus, Switzerland.

Note on Data Access:
The workflow relies on several datasets  that are not publicly available for redistribution. Therefore, this repository does not include raw data. Instead, we provide a detailed list of required datasets and preprocessing instructions so that users with the appropriate data licenses can reproduce the workflow.

```
tranquility_glarus/
├── README.md                 # Project description and instructions
├── TIGL.Rmd                  # Single master R script for full workflow
│
├── data/                     # Input datasets (placeholders only, not included)
│   ├── boundaries/           # Study area boundary and buffers (SwissBOUNDARIES3D)
│   ├── tlm/                  # SwissTLM3D & TLMRegio datasets
│   ├── air_pollution/        # NO2, PM10, PM2.5, Ozone rasters (BAFU)
│   ├── bird_species/         # Swiss Bird Atlas (Vogelwarte)
│   ├── noise/                # Road, rail, aviation noise (BAFU, SIL)
│   ├── light_emission/       # LABES dataset (BAFU)
│   ├── stench/                # Agricultural + features from TLM (waste inciniration plants and wastewater treatment facilities)
│   ├── presence_people/      # Flickr API derived data
│   ├── remoteness/           # LABES accessibility dataset
│   ├── arealstatistik/       # Arealstatistik (swisstopo)
│   └── VM/                   # VisibilityMap©
│
├── outputs/                  # Generated analysis results (empty, created by scripts)
│   ├── rasters/              # Processed tranquility factor rasters
│   ├── combination/          # Final tranquility index maps
│   ├── graphics/             # Histograms, patch plots, visualizations
│   └── patches/              # High-tranquility patch shapefiles + statistics
```

## Data Requirements and Script Description

This script computes the **Tranquility Index** for the canton of Glarus and forms part of my master's thesis *"A participative approach towards modeling tranquility: A case study in Glarus, Switzerland"* at the Department of Geography, University of Zurich (GIUZ). Further methodological details and descriptions can be found in the thesis.  

The following datasets must be obtained and placed in the `/data/` directory structure provided in the repository:  
- **Boundaries:** SwissBOUNDARIES3D (swisstopo)  
- **Topographic Data:** SwissTLM3D & TLMRegio (swisstopo)  
- **Air Pollution:** NO₂, PM₁₀, PM₂.₅, O₃ rasters (BAFU)  
- **Noise:** Road and rail noise (BAFU); aviation noise via SIL perimeter (BAZL)  
- **Light Emission & Remoteness:** LABES datasets  
- **Bird Song:** Swiss Bird Atlas (Vogelwarte)  
- **Land Cover:** Arealstatistik (swisstopo)  
- **Human Presence:** Flickr API (geotagged images; must be collected by user)  

The workflow proceeds in four main steps:  
- **Prepares data:** Loads packages, sets project root, extracts and buffers the Glarus boundary, creates a 100 m raster template, and clips national datasets (TLM, FLOZ, Arealstatistik).  
- **Generates indicators:** Processes forests, streams, lakes, roads, infrastructure, and urbanization with visibility analyses and distance-decay functions. Additional layers include noise, air pollution, light emission, remoteness, bird species, stench, and human presence.  
- **Combines factors:** Normalizes all rasters to 0–100, applies AHP weights, computes positive and negative indices, and aggregates them into the final Tranquility Index.  
- **Analyzes results:** Identifies dominant factors per cell, produces histograms, extracts and characterizes tranquil patches, and cross-tabulates tranquility with land cover.  

**Outputs:** The script saves tranquility rasters, patch shapefiles, and visualizations. The workflow can be adapted to other case studies by adjusting input data, decay parameters, weights and paths.
