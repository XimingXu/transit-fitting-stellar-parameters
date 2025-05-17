# Transit Fitting for Stellar Parameters: Can Exoplanet Transits Improve Our Understanding of Host Star Properties?
## MSc Research Project in Astrophysics at UCL - Ximing Xu
### Overview
This repository contains the code and analysis pipeline for my MSc research project, supervised by Dr. Vincent Van Eylen. This research aims to investigate whether the presence of transiting exoplanets can contribute to a better understanding of the characteristics of their host stars.

- The first part of the project focuses on fitting the TESS light curves of known transiting exoplanets to constrain key transit parameters such as the planet-to-star radius ratio, impact parameter, and stellar density.
- The second part focuses on stellar modeling, which uses the stellar density obtained from transit fitting, combined with additional host star data from the NASA Exoplanet Archive, to improve the characterization of the host stars.

### Methodology
In the transit fitting part, the `lightkurve` package was used to process the TESS light curve data. This included normalizing the flux, removing outliers, and combining data from multiple data sectors. Then, the `juliet` package was used to fit the light curve and constrain exoplanet parameters such as planet-to-star radius ratio and the stellar density of their host stars.

In the stellar modelling part, the `basta` package was used to perform stellar modelling of each host star based on three models. These models share 7 common input parameters (starid, longitude, latitude, parallax, parallax_err, G_Gaia, G_Gaia_err), along with their own specific inputs as shown below.

- Light curve-based model (rho, rho_err)
- Spectroscopy-based model (Teff, Teff_err, FeH, FeH_err)
- Combined model (Teff, Teff_err, FeH, FeH_err, rho, rho_err)

The stellar density data are obtained from the transit fitting part, while the remaining stellar parameters — including galactic coordinates, parallax, Gaia magnitude, effective temperature, and metallicity — can be found in the NASA Exoplanet Archive. When the results from the light curve-based model and the spectroscopy-based model are consistent (i.e., the stellar density derived from light curve fitting is reliable), the combined model can better constrain the stellar parameters.

**Note:** It is highly recommended to run `basta` in a new environment (e.g., Google Colab). Before running the main code, please upload the corresponding model `.py` file and the target `.ascii` file, also make sure the file paths are correct.

### Sample Output
Transit Fitting Result for WASP-17b
<p align="center">
  <img src="example_outputs/transit_fitting_output_1.png" style="width:80%;"/>
</p>
Stellar Modelling Result for WASP-17 (Combined Model)
<p align="center">
  <img src="example_outputs/stellar_modelling_output_combined_model.png" style="width:80%;"/>
</p>

### References
- Aguirre Børsen-Koch, V., Rørsted, J. L., Justesen, A. B., et al. (2021). The Bayesian Stellar Algorithm BASTA: A fitting tool for stellar studies, Asteroseismology, exoplanets, and Galactic Archaeology. *Monthly Notices of the Royal Astronomical Society*, 509(3), 4344–4364. https://doi.org/10.1093/mnras/stab2911
- Espinoza, N., Kossakowski, D., & Brahm, R. (2019). juliet: A versatile modelling tool for transiting and non-transiting exoplanetary systems. *Monthly Notices of the Royal Astronomical Society*, 490(2), 2262-2283. https://doi.org/10.48550/arXiv.1812.08549
- Foreman-Mackey, D. (2016). Corner.py: Scatterplot matrices in Python. The Journal of Open 
Source Software, 1(2), 24. https://doi.org/10.21105/joss.00024
- Lightkurve Collaboration, Cardoso, J. V. d. M., Hedges, C., Gully-Santiago, M., Saunders, N., Cody, A. M., ... Barentsen, G. (2018). Lightkurve: Kepler and TESS time series analysis in Python [Software]. *Astrophysics Source Code Library*. http://adsabs.harvard.edu/abs/2018ascl.soft12013L
