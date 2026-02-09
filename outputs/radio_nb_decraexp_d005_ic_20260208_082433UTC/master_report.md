# Negative-binomial radio dipole audit (arXiv:2509.16732)

Paper-faithful reproduction of the NB counts-in-cells dipole estimator (Eq. 6-8).
All fits include **zero-count** cells inside the survey footprint (Nside=32).

## Config
- created_utc: `2026-02-08T08:26:12.887925+00:00`
- nside: `32` (nest=True)
- NB model: `decra_exp`
- extra templates: `[]`
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
- **NVSS** MAP: d=0.05000, (RA,Dec)=(77.5,-65.9)
  - loglike=-27642.65, AIC=55301.30, BIC=55357.61 (k=8, n=8426)
- **RACS-low** MAP: d=0.05000, (RA,Dec)=(215.6,11.8)
  - loglike=-25515.28, AIC=51046.55, BIC=51101.85 (k=8, n=7427)
- **LoTSS-DR2** MAP: d=0.05000, (RA,Dec)=(111.8,-1.0)
  - loglike=-7227.99, AIC=14471.99, BIC=14514.50 (k=8, n=1502)
- **RACS-low + NVSS** MAP: d=0.04894, (RA,Dec)=(203.1,-44.9)
  - loglike=-53166.35, AIC=106358.70, BIC=106458.42 (k=13, n=15853)
- **LoTSS-DR2 + RACS-low + NVSS** MAP: d=0.05000, (RA,Dec)=(178.0,-44.0)
  - loglike=-60399.23, AIC=120834.46, BIC=120974.17 (k=18, n=17355)

## Notes
- LoTSS: the paper cites an 'inner masked region' from Hale+23 [27]. The public DR2 MOC is a best-effort proxy; small blanked facets are not encoded in the MOC.
- NB overdispersion inflates uncertainties vs Poisson, but it does not itself correct coherent spatial selection/calibration systematics that can mimic a dipole.
- Template basis: `['dec_z', 'dec2_z', 'sin_ra_z', 'cos_ra_z']`
- This run uses an extended stress-test model with exp-modulated nuisance templates in r_i; this is broader than the paper's baseline Eq. 6-8 form.

