# EMIT O₂ A-Band Analysis

This project analyzes NASA EMIT Level 1B hyperspectral radiance to investigate the atmospheric oxygen (O₂) A-band near 760 nm and its relationship with surface elevation.

The goal is to test whether the O₂ absorption signal that is useful in passive atmospheric ranging studies can also be identified and characterized in real orbital imaging-spectroscopy data. Using an EMIT scene acquired over the Republic of Georgia on 3 June 2026, the analysis examines radiance across spectral channels surrounding the O₂ A-band, constructs a continuum-normalized absorption index, maps its spatial variation across the scene, and evaluates how the signal changes with surface elevation.

A strong decrease in continuum-normalized O₂ A-band depth is observed over the 100-2000 m elevation range. Across more than one million valid pixels, the relationship has a pixel-level correlation of **r = -0.874**, while 100-m elevation-bin means produce **r = -0.995** with a slope of approximately **-0.0388 km⁻¹**.

The analysis also evaluates neighboring wavelengths to determine whether the elevation response is spectrally specific. The results show substantial wavelength dependence, providing evidence that the observed relationship is not simply a uniform radiometric trend across all nearby EMIT channels.

This project does **not** demonstrate geometric range retrieval from orbit. EMIT has relatively broad spectral channels compared with the narrow-band configurations used in my passive-ranging research, and the measurements may also be influenced by surface reflectance, atmospheric state, illumination, and viewing geometry. Instead, this work serves as an observational proof of concept showing that the O₂ A-band is clearly detectable in real orbital radiance and contains systematic sensitivity to atmospheric column length.

## Research Question

Can the atmospheric O₂ A-band near 760 nm be detected in NASA EMIT orbital radiance, and does its measured absorption strength vary systematically with surface elevation?

## Data

- Instrument: NASA EMIT
- Product: Level 1B radiance
- Acquisition date: 3 June 2026
- Study region: Republic of Georgia
- Spectral region analyzed: approximately 730–800 nm
- Primary O₂-sensitive channel: 760.45 nm
- Reference channel: 775.37 nm

## Methods

The workflow includes:

1. Reading EMIT L1B hyperspectral radiance data with Python.
2. Extracting spectral channels surrounding the O₂ A-band.
3. Examining the at-sensor radiance spectrum around 760 nm.
4. Computing an O₂ absorption index using the 760.45 nm and 775.37 nm channels.
5. Mapping the spatial distribution of the index across the EMIT scene.
6. Comparing continuum-normalized O₂ A-band depth with surface elevation.
7. Binning pixels into 100-m elevation intervals.
8. Evaluating wavelength-dependent elevation sensitivity across neighboring spectral channels.

## Key Results

For pixels between 100 and 2000 m elevation:

- Pixel-level correlation: **r = -0.874**
- 100-m-bin correlation: **r = -0.995**
- Elevation sensitivity: **-0.0388 km⁻¹**
- Number of analyzed pixels: **1,034,046**

The O₂ A-band signal decreases systematically with increasing surface elevation, consistent with a reduction in atmospheric column length above higher terrain.

## Interpretation

The results show that the atmospheric O₂ A-band is clearly measurable in EMIT L1B radiance and that its strength varies systematically with elevation. This provides a useful observational bridge between orbital imaging spectroscopy and passive-ranging approaches based on oxygen absorption.

The neighboring-channel analysis also shows that elevation sensitivity varies substantially with wavelength, indicating that the observed behavior is spectrally structured rather than identical across the surrounding continuum.

## Limitations

This experiment should not be interpreted as a demonstration of orbital geometric range retrieval. Important limitations include:

- EMIT's spectral channels are much broader than the narrow bands used in optimized passive-ranging systems.
- Surface reflectance can influence measured radiance.
- Atmospheric aerosol and water-vapor conditions may introduce additional variability.
- Solar illumination and viewing geometry may affect the observed signal.
- Elevation is used here as a proxy for atmospheric-column differences rather than direct sensor-to-target range.

The project is therefore best interpreted as a proof-of-concept analysis of O₂ A-band sensitivity in real orbital hyperspectral measurements.

## Repository Structure

```text
emit-o2-aband-analysis/
├── README.md
├── LICENSE
├── requirements.txt
├── notebooks/
│   └── EMIT_O2_ABand_Analysis.ipynb
└── figures/
    ├── 01_radiance_spectrum.png
    ├── 02_o2_index_map.png
    ├── 03_o2_vs_elevation.png
    └── 04_spectral_elevation_sensitivity.png


And finally:

```md
## Tools

Python, NumPy, Pandas, Xarray, SciPy, Matplotlib, NetCDF4, and Jupyter.

## Data Availability

The original NASA EMIT data are not redistributed in this repository. The notebook is designed to operate on locally downloaded EMIT products.

## Author

Tamta Burduli  
B.S. Physics, Arizona State University  
Research interests: remote sensing spectroscopy, hyperspectral imaging, atmospheric absorption, and passive ranging
