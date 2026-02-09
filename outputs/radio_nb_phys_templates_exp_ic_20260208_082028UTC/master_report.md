# Negative-binomial radio dipole audit (arXiv:2509.16732)

Paper-faithful reproduction of the NB counts-in-cells dipole estimator (Eq. 6-8).
All fits include **zero-count** cells inside the survey footprint (Nside=32).

## Config
- created_utc: `2026-02-08T08:24:18.574544+00:00`
- nside: `32` (nest=True)
- NB model: `decra_exp`
- extra templates: `['haslam_k408', 'nvss_e_s1_4', 'lotss_isl_rms', 'lotss_masked_fraction', 'lotss_moc_frac']`
- galactic cut: `|b| >= 10.0 deg`
- LoTSS MOC mode: `full` (lmax=10)
- template controls: coef_bound=0.2, ridge=1.0
- do_mcmc: `False` / executed: `False` (walkers=48, burn=600, step=1400)
- multistart: n_starts=64, start_seed=20260208

## Footprints / overdispersion (p from empirical mean/var)
- **NVSS** cut=20.0 mJy: cells=8426, Nsrc=266836, mu=31.67, var=43.86, p=0.278018
- **RACS-low** cut=20.0 mJy: cells=7427, Nsrc=332052, mu=44.71, var=56.88, p=0.213913
- **LoTSS-DR2** cut=5.0 mJy: cells=1502, Nsrc=444703, mu=296.07, var=915.11, p=0.676459

## Fits
- **NVSS** MAP: d=0.05000, (RA,Dec)=(83.2,-69.1)
  - loglike=-27611.21, AIC=55248.41, BIC=55339.92 (k=13, n=8426)
- **RACS-low** MAP: d=0.05000, (RA,Dec)=(221.9,14.7)
  - loglike=-25507.00, AIC=51040.01, BIC=51129.87 (k=13, n=7427)
- **LoTSS-DR2** MAP: d=0.05000, (RA,Dec)=(107.3,-0.8)
  - loglike=-7136.89, AIC=14299.78, BIC=14368.87 (k=13, n=1502)
- **RACS-low + NVSS** MAP: d=0.04997, (RA,Dec)=(213.5,-49.7)
  - loglike=-53125.20, AIC=106296.40, BIC=106472.83 (k=23, n=15853)
- **LoTSS-DR2 + RACS-low + NVSS** MAP: d=0.05000, (RA,Dec)=(188.6,-53.3)
  - loglike=-60266.14, AIC=120598.27, BIC=120854.41 (k=33, n=17355)

## Notes
- LoTSS: the paper cites an 'inner masked region' from Hale+23 [27]. The public DR2 MOC is a best-effort proxy; small blanked facets are not encoded in the MOC.
- NB overdispersion inflates uncertainties vs Poisson, but it does not itself correct coherent spatial selection/calibration systematics that can mimic a dipole.
- Template basis: `['dec_z', 'dec2_z', 'sin_ra_z', 'cos_ra_z', 'haslam_k408_z', 'nvss_e_s1_4_z', 'lotss_isl_rms_z', 'lotss_masked_fraction_z', 'lotss_moc_frac_z']`
- This run uses an extended stress-test model with exp-modulated nuisance templates in r_i; this is broader than the paper's baseline Eq. 6-8 form.

