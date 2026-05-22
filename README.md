# Ultraviolet Spectral Analysis Using Astropy

## Overview
This project demonstrates a complete workflow for analyzing astronomical spectral data using Python and Astropy. The analysis focuses on ultraviolet (UV) spectral observations from the International Ultraviolet Explorer (IUE) of a region in the galaxy NGC 4151.
This project recreates key steps used in astrophysical research, including data extraction, cleaning, reconstruction of wavelength arrays, and identification of spectral features.

## Goals
- Process real astronomical FITS data
- Extract and interpret spectral information (flux vs. wavelength)
- Apply data cleaning using quality flags
- Visualize and analyze trends and spectral features
- Simulate a simplified version of modern astronomical data pipelines

## Dataset
- Source: NASA FITS sample data (IUE LWP spectrum)
- Target: Region in NGC 4151 (active galaxy nucleus)
- Data type: Ultraviolet spectrum
- Format: FITS binary table

## Tools & Libraries
- Python
- NumPy
- Matplotlib
- Astropy
- SciPy

## Methods
### 1. Data Loading
- Opened FITS file using astropy.io.fits
- Inspected file structure and metadata
### 2. Data Extraction
- Extracted:
  - Flux values (energy received per wavelength)
  - Starting wavelength
  - Wavelength step size (DELTAW)
  - Data quality flags
### 3. Wavelength Reconstruction
Wavelength values were reconstructed using metadata:
`wavelength = wavelength_start + np.arange(len(flux)) * delta_w`  
This approach mirrors how many astronomical instruments store spectral data efficiently.
### 4. Data Cleaning
- Removed invalid data points using quality flags:
`mask = (quality == 0)`
- Filtered arrays to ensure only reliable data was analyzed
### 5. Visualization
- Generated plots of:
  - Flux vs. wavelength
  - Normalized flux
- Applied smoothing for clarity
### 6. Feature Detection
- Identified spectral peaks using:
`np.argmax(flux_clean)`
- Refined detection by excluding noisy edge regions

## Results
The processed spectrum reveals key features:
- A stable continuum region between ~2000-2700 Å
- Increased noise at shorter wavelengths (~1800 Å)
- A localized feature near 2800 Å, possible indicating an emission or absorption line
- A rising trend at longer wavelengths (~3000-3400 Å)
These patterns are consistent with real observational spectral data, which often includes noise and instrument-dependent effects.

## Interpretation
- The noisy region near 1800 Å likely reflects low signal-to-noise or instrument limitations
- The smoother mid-range indicates reliable continuum emission
- The feature near 2800 Å may correspond to atomic transitions or spectral lines
- The increasing flux at longer wavelengths may indicate changes in emission intensity or continuum slope
