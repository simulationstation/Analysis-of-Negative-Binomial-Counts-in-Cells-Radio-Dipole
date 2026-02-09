# Negative-binomial radio dipole audit (arXiv:2509.16732)

Paper-faithful reproduction of the NB counts-in-cells dipole estimator (Eq. 6-8).
All fits include **zero-count** cells inside the survey footprint (Nside=32).

## Config
- created_utc: `2026-02-08T07:31:02.292704+00:00`
- nside: `32` (nest=True)
- NB model: `decra_linear`
- galactic cut: `|b| >= 10.0 deg`
- LoTSS MOC mode: `full` (lmax=10)
- template controls: coef_bound=1.5, ridge=0.0
- do_mcmc: `False` / executed: `False` (walkers=48, burn=600, step=1400)
- multistart: n_starts=32, start_seed=20260208

## Footprints / overdispersion (p from empirical mean/var)
- **NVSS** cut=20.0 mJy: cells=8426, Nsrc=266836, mu=31.67, var=43.86, p=0.278018
- **RACS-low** cut=20.0 mJy: cells=7427, Nsrc=332052, mu=44.71, var=56.88, p=0.213913
- **LoTSS-DR2** cut=5.0 mJy: cells=1502, Nsrc=444703, mu=296.07, var=915.11, p=0.676459

## Fits
- **NVSS** MAP: d=0.01500, (RA,Dec)=(167.9,-6.9)
- **RACS-low** MAP: d=0.01500, (RA,Dec)=(167.9,-6.9)
- **LoTSS-DR2** MAP: d=0.01500, (RA,Dec)=(167.9,-6.9)
- **RACS-low + NVSS** MAP: d=0.01500, (RA,Dec)=(167.9,-6.9)
- **LoTSS-DR2 + RACS-low + NVSS** MAP: d=0.01500, (RA,Dec)=(167.9,-6.9)

## Notes
- LoTSS: the paper cites an 'inner masked region' from Hale+23 [27]. The public DR2 MOC is a best-effort proxy; small blanked facets are not encoded in the MOC.
- NB overdispersion inflates uncertainties vs Poisson, but it does not itself correct coherent spatial selection/calibration systematics that can mimic a dipole.
- This run uses a linear nuisance-template extension in r_i (dec, dec^2, sinRA, cosRA) with bounded coefficients; this is a controlled stress test around the paper baseline.
- Injection/recovery ran with nsim=80, d_inj=0.01735, (RA,Dec)=(167.94,-6.94).
- Injection summary: pure axis err p50=63.37 deg vs template-linear axis err p50=0.00 deg.

