# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Educational Jupyter notebook repository for the pyOpenMS Course, reusable across training events, workshops, and self-paced learning. Teaches proteomics data analysis workflows using mass spectrometry data processing, peptide identification, and quantification with pyOpenMS.

## Commands

```bash
# Install dependencies
pip install -r requirements.txt

# Or with conda
conda create -n pyopenms_course python=3.10
conda activate pyopenms_course
pip install -r requirements.txt

# Start JupyterLab
jupyter lab

# Start classic Notebook
jupyter notebook
```

No build, test, or lint configuration exists - this is purely educational notebook content.

## Architecture

### Notebook Structure
The notebooks in `notebooks/` follow a sequential learning path:
1. **PyOpenMS_Task1_Peaks.ipynb** - Protein digestion, MS1 visualization, isotope patterns, TIC
2. **PyOpenMS_Task2_ID.ipynb** - Peptide database search, fragment spectrum generation, alignment, scoring
3. **PyOpenMS_Task3_Quant.ipynb** - Feature detection (Biosaur2), ID mapping, interactive visualization

### Core Pattern
All notebooks follow the standard PyOpenMS workflow:
```python
import pyopenms as oms

# Load data
data = oms.DataType()
oms.FileFormat().load("file.xyz", data)

# Process with algorithm
algorithm = oms.Algorithm()
result = oms.ResultType()
algorithm.run(data, result)

# Export to pandas for analysis
df = result.get_df()
```

### Data Formats
- **mzML**: Mass spectrometry raw data
- **FASTA**: Protein sequence databases
- **idXML**: OpenMS peptide identification results
- **featureXML**: OpenMS feature maps

Notebooks download data files on-demand during execution (some are large, ~700MB).

## Key Dependencies

- **pyopenms** (>=3.5.0): Mass spectrometry processing (C++ Python bindings)
- **pyopenms-viz** (>=1.0.0): MS-specific visualization
- **numpy/pandas/scipy**: Scientific computing
- **matplotlib/seaborn/plotly**: Visualization
