# Analysis of Negative-Binomial Counts-in-Cells Radio Dipole

Clean, standalone repository for the software and manuscript used to audit the
negative-binomial (NB) counts-in-cells radio dipole analysis.

## Repository layout

- `scripts/run_radio_nb_dipole_audit.py`
  - Main NB dipole audit (single-survey + joint fits, optional template stress tests,
    optional MCMC, and injection/recovery).
- `scripts/run_radio_combined_same_logic_audit.py`
  - Companion combined radio same-logic robustness audit.
- `radio_a/main.tex`
  - REVTeX 4.2 PRD-style manuscript for the radio NB identifiability note.
- `radio_a/make_figures.py`
  - Rebuilds manuscript figures from pinned JSON run outputs.
- `outputs/radio_nb_*`
  - Pinned JSON outputs used for figure generation and reproducibility.

## Software and related DOIs

- Software archive for this radio NB audit: `10.5281/zenodo.18530376`
- Parent Quasars-Systematics archive: `10.5281/zenodo.18476711`
- Related external products used in the study:
  - NVSS: `10.1086/300337`
  - RACS DR1: `10.1017/pasa.2020.41`
  - LoTSS-DR2: `10.1051/0004-6361/202142484`
  - LoTSS-DR2 data products: `10.25606/SURF.LoTSS-DR2`
  - Remazeilles 408 MHz map: `10.1093/mnras/stv1274`

## Install

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Rebuild figures

```bash
python radio_a/make_figures.py
```

## Compile manuscript

```bash
pdflatex -interaction=nonstopmode -output-directory=radio_a radio_a/main.tex
pdflatex -interaction=nonstopmode -output-directory=radio_a radio_a/main.tex
```

## Data paths for full reruns

The scripts expect locally staged survey files (not committed here), with defaults:

- `data/external/zenodo_6784602/secrest_extracted/secrest+22_accepted/nvss/reference/NVSS.fit`
- `data/external/radio_dipole/racs_low/racs_low_dr1_sources_galacticcut_v2021_08_v02_mincols.csv.gz`
- `data/external/radio_dipole/lotss_dr2/LoTSS_DR2_v110_masked.srl.fits`
- `data/external/radio_dipole/lotss_dr2/dr2-moc.moc`
I present evidence that this anomaly is a systematics artifact rather than physical occurrence. 
