# Compliance Mismatch Drives Mechanochemical Reactivity in Diels-Alder Reactions

Analysis notebook and supporting data for the manuscript by Mark A. Boyer,
Ryan Kwok, Tzu-Hsuan Chao, Yeu-Shiuan Ho, Nicholas Hopper, Mateusz Marianski,
and Daniel P. Tabor, in manuscript author order.

The analysis examines how molecular compliance and deformation affect
force-modified Diels–Alder reaction barriers, and compares directed forces
with hydrostatic pressure.

## Repository contents

| Path | Contents |
| --- | --- |
| `DA_paper/DA_figs.ipynb` | Figure-analysis notebook copied from the paper workspace |
| `DA_paper/compressed_datasets/` | Force-response datasets, including compressed and expanded archives; supplied separately |
| `DA_paper/pressure/` | Hydrostatic-pressure spreadsheets and CSV inputs |
| `DA_paper/pressure_outputs/` | Pressure geometry archives and RMSD tables; `.npz` archives supplied separately |
| `DA_paper/*compliances*.npz` | Compliance data; supplied separately |
| `DA_paper/*volum*.npz` | Activation volumes and volumes along reaction coordinates; supplied separately |
| `DA_paper/random_force_pairwise_rmsds.npz` | Saved pairwise RMSD calculations; supplied separately |
| `DA_paper/figs/pressure_force_reproduction/` | Saved inputs, layout, provenance, and four exported pressure/force panels; `.npz` input supplied separately |
| `gamma_escans_derivs*.json` | Gamma-coordinate and force-scan data; supplied separately |
| `disub_alt.npz` | Reference data used in the DFT comparison; supplied separately |
| `DATA_MANIFEST.csv` | Repository-relative paths, byte counts, and SHA-256 checksums of the separately distributed files |

## Obtaining the data

**Zenodo data record: link to be added before release.**

Large `.npz` archives and gamma-scan JSON datasets are excluded from Git and
must be downloaded separately. Restore each file to the exact path in
`DATA_MANIFEST.csv`, relative to this repository's root. For example,
`DA_paper/compressed_datasets/product_library_cyclop_b97_expanded.npz`
belongs in that directory, while `gamma_escans_derivs_expanded.json` belongs
at the repository root. Preserve these paths if packaging the data in an archive.
The manifest provides the expected size and checksum for each file.

The ignore rules do not delete local data. Small JSON files containing
provenance and figure-layout settings remain part of the repository.
GitHub's automatic Zenodo archive contains the committed files; separately
distributed datasets must also be uploaded to the data record.

## Using the notebook

Open `DA_paper/DA_figs.ipynb` with the working directory set to `DA_paper/`.
Its relative input paths depend on this layout. The dataset loader prefers
`*_expanded.npz` when available and otherwise loads the corresponding `.npz`.

The notebook depends on the research versions of `cmcc_reactions`, `McUtils`,
and `Psience`, as well as scientific Python packages including NumPy, RDKit,
and pandas. Plotting and spreadsheet reading also require their supporting
packages. This repository does not yet provide a pinned or independently
validated installation environment.

The notebook is a working research notebook with exploratory cells,
incomplete expressions, and intermediate state; it is not a validated
top-to-bottom reproduction script. Some cells retain local absolute paths,
including the original location of `disub_alt.npz` and a diagnostic input at
`/Users/Mark/Downloads/pipeline_data_rigid_useint.json`. The latter is outside
the source data collection and is not included here. Select the relevant
analysis sections and adjust local paths before running them.

The final pressure/force reproduction section uses the saved
`figs/pressure_force_reproduction/input_data.npz`, `equation_layout.json`, and
`provenance.json` to regenerate four panels. It explicitly checks for ARM
Python 3.11 and local research source directories; those paths must be
configured for the machine used. Existing panel exports are included for
reference. No notebook execution or independent figure reproduction was
performed as part of repository preparation.

## Citation and metadata

`CITATION.cff` provides citation information for the analysis archive.
`.zenodo.json` provides corresponding Zenodo release metadata. Author names,
order, affiliations, and the manuscript title were transcribed from the
paper's `DA_paper/DA_Text/Main.tex` in the original workspace; the manuscript
source is not included in this repository.

Zenodo uses `.zenodo.json` in preference to `CITATION.cff` when both are
present, while GitHub can display a citation from `CITATION.cff`. Keep the
two files consistent when updating the title, authors, or release details.
See the [Zenodo metadata documentation](https://help.zenodo.org/docs/github/describe-software/zenodo-json/).

## Before the first release

- Add the Zenodo data record link above and upload the files listed in
  `DATA_MANIFEST.csv`. If their contents change, update their checksums.
- Choose the code and data licenses, add the appropriate license text, and
  record the selected licenses in the citation and Zenodo metadata. No
  license has been inferred or granted by this preparation.
- Add the confirmed archive version, release date, and DOI to the metadata.
  If code and data have separate records, identify both records and their
  relationship in Zenodo and in this README.
- Add the associated paper's confirmed citation/DOI when available; no
  publication status, journal, DOI, or ORCID has been assumed.
- Validate the intended figure workflow in the release environment and
  document the required research-package versions and path changes.

