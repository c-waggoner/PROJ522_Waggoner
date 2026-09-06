# Sentinel-3 Astaxanthin Anomaly Detection (Irish & Celtic Seas)

This repository contains the processing pipeline and analysis code for detecting astaxanthin pigment anomalies from Sentinel-3 OLCI imagery in Irish and Celtic Sea waters, and testing whether those anomalies relate to in situ CPR-recorded *Calanus finmarchicus* and *C. helgolandicus* abundance. Part of an MSc dissertation project, PROJ522.

## Files

### `Sentinel3_CPR_Pipeline.ipynb`
Stage 1. Downloads Sentinel-3 OLCI L2 WFR scenes for every CPR sample date, applies the water-quality flag mask (including land), and crops a 4 km box of all twelve OLCI visible/NIR bands around each CPR point, saving both raw swath pixels and a display grid per box.

### `DE2000_CPR_Matchup.ipynb`
Stage 2. Converts the cropped Rrs boxes to standardised eRGB, matches every valid pixel against the Case 2 and Case 2 + Calanus look-up tables using DE2000 colour difference, and joins the resulting satellite anomaly values to in situ CPR abundance (AEI) for correlation, detection, and sensitivity analysis.

### `CPR_ROI.xlsx`
Continuous Plankton Recorder sampling points defining the region of interest used to search for and download matching Sentinel-3 scenes in `Sentinel3_CPR_Pipeline.ipynb`. Covers 12.5°W to 4.5°W and 48.5°N to 56°N from 2018 to 2022, for all Calanoid species. Includes recorded abundances and AEI values for Calanus I-IV, *Calanus finmarchicus*, *C. helgolandicus*, and *Centropages typicus*, which are joined back to the satellite results in the matchup notebook.
