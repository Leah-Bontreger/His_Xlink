# UV-Visible Absorbance Spectral Deconvolution

## Purpose
To understand what chemical species are contributing to an observed novel absorbance in the UV-vis spectrum of a peptide mixture. The deconvoluted peaks should be based from actual chemical spectra instead of calculating the best mathematical fit.
## Chemistry Background
[UV-Visible Spectroscopy](https://chem.libretexts.org/Bookshelves/Analytical_Chemistry/Physical_Methods_in_Chemistry_and_Nano_Science_(Barron)/04%3A_Chemical_Speciation/4.04%3A_UV-Visible_Spectroscopy) is a very common analysis in chemistry labs to quantify solution concententrations, monitor reaction progess, and understand the chemical structures and complexes in a solution. UV-vis absorbance bands are symmetrical and can be described mathematically by a Gaussian function. Spectra that do not have distinct, symmetric bands means that the absorbance bands are overlapped which will obscure individual peak's height, width, and center. Calculation of extinction coefficients from overlapped bands will lead to error, particularly leading to overestimation of sample concentrations. 

A peptide HHGY was oxidized to oxHHGY, which produced a novel UV-Vis absorbance. "oxHHGY" refers to the mixture of oxidized peptide products that cannot be separated on a large scale. Researchers wanted to know what chemical structure or complex was causing oxHHGY's novel absorbance. This was made difficult by the overlapped UV-Vis spectrum of oxHHGY. Multi-Gaussian spectral deconvolution was used to characterize the individual peaks  in the oxHHGY standard curve. [Spectal deconvolution processes](https://www.sciencedirect.com/science/article/pii/S1386142514018836) have been utilized before by researchers in MATLAB language to resolve sub-bands in a UV-vis sample. For the present study however, researchers opted for deconvolution in Python language because it is free and widely used.
## Methodology
A mathematical model can be used to perfectly fit experimental data given enough curves. However, the curves fit to the data may not have a physical basis. Therefore it is best-practice to provide good "guesses" for the model to fit the data based on actual chemical absorbances. To accomplish this, preliminary spectral deconvolution of individual species provided good guesses for the spectral deconvolution of the peptide mixtures. The data for this deconvolution process was collected as follows:

1. oxHHGY peptide mixture was separated via Agilent Triple Quad Liquid Chromatography - Mass Spectrometry (LC-MS) equipped with a reversed-phase Kinetex column and photodiode array detector. This separated the mixture into 28 peptide species.
2. UV-vis spectra were extracted for each peptide species.
3. These spectra, which had minimal peak overlap, were fit with 1-3 peaks in the "Individual_spectral_deconvolution" notebook.
4. A standard curve of the oxHHGY peptide mixture was made via 2-fold serial dilution of the sample and measure in a 1 cm quart cuvette on a Varian Cary 50 UV/visible spectrophotometer.
5. In the notebook "StandardCurve_Deconvolution," the dilutions of the standard curve were fit using the peak parameters calculated in the first notebook to provide good guesses and bounds that could be associated with actual chemical structures.
6. Fit peak data was used to calculate extinction coefficients. The peaks' absorbances were plot against an accurately calculated concentration for each dilution of the standard curve. Trendlines of this data revealved extinction coefficients and high R squared values


## Conclusions
Individual absorbance bands were resolved by this procedure, which allowed for better estimation of sample contration and calculation of extinction coefficients. When the spectral data was matched with the mass spectrometer, it was revealed that oxygenated, crosslinked, and multimerized peptides were the primary contributors to oxHHGY's novel absorbance.
## References
This code supports the conclusions reported in ["Intramolecular Histidine Cross-Links Formed via Copper-Catalyzed Oxidation of Histatin Peptides"](https://pubs.acs.org/doi/10.1021/jacs.5c01363) by Bontreger et al.

References consulted include:
-  Eric Monson, Ph.D., data visualization analyst at Duke University Libraries' Center for Data and Visualization Sciences
- https://stackoverflow.com/questions/54851012/fitting-data-with-multiple-gaussian-profiles-in-python
- [Excel for Chemists: a Comprehensive Guide by E. Joseph Billo, 1997, Chapter 19 Analysis of Spectrophotometric Data](https://afitch.sites.luc.edu/Articles/DeLevie%20Deconvolution%20spectra%20excel.pdf)
