# Reviewer Reproducibility Package

This anonymous package accompanies a NeurIPS Evaluations & Datasets submission
on country-level frontier AI exposure. It is designed for reviewer inspection:
the scripts validate the released derived tables and reproduce paper-facing
values, regression tables, and release-supported figures from those tables
where redistribution permits.

## Quickstart

```bash
python3 -m venv /tmp/jagged-economy-reviewer-venv
source /tmp/jagged-economy-reviewer-venv/bin/activate
pip install -r requirements.txt

make validate
make reproduce
make notebooks
make check-upload
```

Expected runtime on a laptop is under a few minutes. All commands are CPU-only
and do not train models.

## What Is Included

- `data/`: derived measured CSV tables used for the paper.
- `metadata/`: manifest, data dictionary, source-data manifest, checksums, and
  expected output inventory.
- `scripts/`: validation, table generation, figure generation, notebook
  execution, and upload-readiness checks.
- `notebooks/`: two clean notebooks for dataset inspection and main-result
  reproduction.
- `PROVENANCE.md`: source/release scope note for why raw files are documented
  but not redistributed.

## What Is Not Included

Raw third-party files and API mirrors are not redistributed. The source-data
manifest lists the source datasets and URLs used to construct the derived
tables. Non-release draft folders and exploratory analysis directories are not
part of this reviewer package. The Microsoft AI Diffusion country-level
extracted table is not redistributed; the package includes aggregate Microsoft
regression summaries and links to the source report. Hosseini Maasoum and
Lichtinger transformed score vectors are also not redistributed; the package
includes aggregate robustness statistics and source links only.

## Reproducibility Scope

The target is paper-output reproducibility from released derived data, not a
raw-source rebuild. This is the appropriate reviewer-facing path because several
inputs are third-party datasets with separate access, licensing, or size
constraints.

Generated tables are value-equivalent reviewer tables. They are intended to
verify the numbers in the paper, not to reproduce the exact camera-ready
Overleaf layout byte-for-byte. The national exposure map is supported by the
released `data/aggregates/national_exposure_map_data.csv` table and generated
national exposure score table; the package does not redistribute map boundary
assets or attempt to recreate the exact Overleaf map layout.
