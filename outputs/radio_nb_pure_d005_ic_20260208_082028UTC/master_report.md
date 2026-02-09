# Negative-binomial radio dipole audit (arXiv:2509.16732)

Paper-faithful reproduction of the NB counts-in-cells dipole estimator (Eq. 6-8).
All fits include **zero-count** cells inside the survey footprint (Nside=32).

## Config
- created_utc: `2026-02-08T08:20:47.046738+00:00`
- nside: `32` (nest=True)
- NB model: `pure`
- extra templates: `[]`
- galactic cut: `|b| >= 10.0 deg`
- LoTSS MOC mode: `full` (lmax=10)
- template controls: coef_bound=1.5, ridge=0.0
- do_mcmc: `False` / executed: `False` (walkers=48, burn=600, step=1400)
- multistart: n_starts=64, start_seed=20260208

## Footprints / overdispersion (p from empirical mean/var)
- **NVSS** cut=20.0 mJy: cells=8426, Nsrc=266836, mu=31.67, var=43.86, p=0.278018
- **RACS-low** cut=20.0 mJy: cells=7427, Nsrc=332052, mu=44.71, var=56.88, p=0.213913
- **LoTSS-DR2** cut=5.0 mJy: cells=1502, Nsrc=444703, mu=296.07, var=915.11, p=0.676459

## Fits
- **NVSS** MAP: d=0.01980, (RA,Dec)=(146.2,20.7)
  - loglike=-27652.71, AIC=55313.42, BIC=55341.58 (k=4, n=8426)
- **RACS-low** MAP: d=0.01914, (RA,Dec)=(185.1,-17.3)
  - loglike=-25532.63, AIC=51073.26, BIC=51100.91 (k=4, n=7427)
- **LoTSS-DR2** MAP: d=0.05000, (RA,Dec)=(122.6,-33.6)
  - loglike=-7238.12, AIC=14484.23, BIC=14505.49 (k=4, n=1502)
- **RACS-low + NVSS** MAP: d=0.01733, (RA,Dec)=(168.8,1.6)
  - loglike=-53189.79, AIC=106389.58, BIC=106427.93 (k=5, n=15853)
- **LoTSS-DR2 + RACS-low + NVSS** MAP: d=0.02054, (RA,Dec)=(152.9,-6.2)
  - loglike=-60451.31, AIC=120914.61, BIC=120961.18 (k=6, n=17355)

## Notes
- LoTSS: the paper cites an 'inner masked region' from Hale+23 [27]. The public DR2 MOC is a best-effort proxy; small blanked facets are not encoded in the MOC.
- NB overdispersion inflates uncertainties vs Poisson, but it does not itself correct coherent spatial selection/calibration systematics that can mimic a dipole.

