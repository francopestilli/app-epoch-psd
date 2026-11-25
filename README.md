# Power Spectral Density on epoched data

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Computes the power spectral density of epoched MEG/EEG data per channel type (gradiometers, magnetometers, EEG) with the MNE-Python multitaper method, with PSD plots.**

Reads MNE epochs, computes the multitaper PSD (mne.time_frequency.psd_multitaper) separately for grad, mag and EEG channels within the chosen frequency and time range, averages across epochs, converts to dB and saves one TSV (channels x frequencies) per channel type plus figures. Use it to inspect spectral content of epoched data. Only channel types present in the data produce output.

| | |
|---|---|
| 📥 **Inputs** | `neuro/meeg/mne/epochs` |
| 📤 **Outputs** | `neuro/meeg/psd` ×3 · `raw` |
| 🐳 **Container** | `brainlife/mne:0.23dev` |
| ⚙️ **Resources** | 8 CPUs · 0.17 h walltime |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.587](https://doi.org/10.25663/brainlife.app.587) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `megfif` | `neuro/meeg/mne/epochs` (epochs) | yes | Epoched MEG/EEG data in MNE -epo.fif format. |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `out_psd_grad` | `neuro/meeg/psd` | psd.tsv with the epoch-averaged gradiometer PSD in dB (channels x frequencies). |
| `out_psd_mag` | `neuro/meeg/psd` | psd.tsv with the epoch-averaged magnetometer PSD in dB (channels x frequencies). |
| `out_psd_eeg` | `neuro/meeg/psd` | psd.tsv with the epoch-averaged EEG PSD in dB, uV^2/Hz (channels x frequencies). |
| `out_figs` | `raw` | PNG figures of the PSD (psd_mne.png and psd_computed.png). |

<details>
<summary><b>⚙️ Parameters</b> (10)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `fmin` | number | `0` | Min frequency of interest. |
| `fmax` | number | `100` | Max frequency of interest. |
| `tmin` | number |  | Min time of interest. |
| `tmax` | number |  | Max time of interest. |
| `bandwidth` | number | `4` | The bandwidth of the multi taper windowing function in Hz. The default value is a window half-bandwidth of 4. |
| `adaptive` | boolean | `false` | Use adaptive weights to combine the tapered spectra into PSD (slow, use n_jobs >> 1 to speed up computation). |
| `low_bias` | boolean | `true` | Only use tapers with more than 90% spectral concentration within bandwidth. |
| `normalization` | enum | `full` | Either “full” or “length” (default). If “full”, the PSD will be normalized by the sampling rate as well as the length of the signal (as in nitime). Options: `full`, `length`. |
| `proj` | boolean | `false` | Apply SSP projection vectors. |
| `picks` | string | `None` | Not read: the code always sets picks to None and processes grad, mag and EEG channels separately. |

</details>

📚 **References used by this App:**
- Gramfort A, et al. MEG and EEG data analysis with MNE-Python. Front Neurosci 7:267 (2013). [doi:10.3389/fnins.2013.00267](https://doi.org/10.3389/fnins.2013.00267)

<!-- brainlife-app:end -->

[![Abcdspec-compliant](https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg)](https://github.com/brain-life/abcd-spec)
[![Run on Brainlife.io](https://img.shields.io/badge/Brainlife-bl.app.587-blue.svg)](https://doi.org/10.25663/brainlife.app.587)

## Documentation
This Brainlife App computes Power Spectral Density (PSD) on MEG epoched data using MNE-Python multitaper method with `mne.time_frequency.psd_multitaper` function.

## Authors
- [Guiomar Niso](guiomar.niso@ctb.upm.es), Instituto Cajal, CSIC, Spain

## Citations
We kindly ask that you cite the following articles when publishing papers and code using this app. 

1. **brainlife. io: A decentralized and open source cloud platform to support neuroscience research**. Hayashi, S., Caron, B. A., et al. & Pestilli, F. (2023). ArXiv. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10274934/

2. **MEG and EEG data analysis with MNE-Python**. Gramfort A, et al. & Hämäläinen MS. (2013). Frontiers in Neuroscience, 7(267):1–13, 2013. https://doi.org/10.3389/fnins.2013.00267

## Funding Acknowledgement
brainlife.io is publicly funded and for the sustainability of the project we kindly ask that you acknowledge the following funding sources:

[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-1636893](https://img.shields.io/badge/NSF_BCS-1636893-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-ACI-1916518](https://img.shields.io/badge/NSF_ACI-1916518-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1916518)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NIH-NIBIB-R01EB030896](https://img.shields.io/badge/NIH_NIBIB-R01EB030896-green.svg)](https://grantome.com/grant/NIH/R01-EB030896-01)


#### MIT Copyright (c) 2021 brainlife.io The University of Texas at Austin and Indiana University
