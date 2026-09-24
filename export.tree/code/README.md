# PKUEEG code

preprocessing/preprocess_pkueeg.py: EEG processing entry point; config/ is beside it.
feature_extraction/stimulus_features/extract_word_level_bert.py: legacy BERT extraction.
validate_layout.py: read-only structure, metadata and array-header checks.
run_bids_validation.py: external BIDS-validator runner; not a scientific analysis.
config/release_scope.json: components included or deferred in this release.
model_downloads/: official-model integration status.
provenance/legacy_layout/: unchanged original builders and verifiers; do not run against this layout.

Use an external environment. requirements.txt currently lists only mne, numpy
and scipy; it is not a complete runnable environment. The default FastICA path
also needs scikit-learn, and the BERT extractor needs torch and transformers.
These dependencies and model revisions have not been added or pinned by the
metadata/documentation correction. Defaults locate the dataset
relative to each script, not the shell working directory. Generated outputs go
beside, not inside, the release. When running a code-only checkout, use explicit
input paths (--bids-root or --word-boundary-dir) and an external --output-root/--output-dir.
This update adapts paths only; it does not claim numerical reproduction or correct
all historical algorithmic limitations. Internal checking reports are maintained
outside the public release.

Known limitations remain: case-sensitive montage/bad-channel matching in the EEG
entry point, no bad-segment rejection or saved per-session ICA records, and a
terminal-window mismatch between the BERT extractor and some released word-level
arrays. model_downloads/ is a status-only directory.

Behavioral accuracy and technical-validation analyses/results are deferred to a
future update. Structural/BIDS checks remain available and do not perform ISC,
TRF, behavioral correlations or decoding analyses. They enforce the current
release scope without treating deliberately deferred components as missing.

Write all checking reports outside the dataset directory, for example:

```bash
python code/validate_layout.py --report ../pkueeg_checks/layout_audit.json
python code/run_bids_validation.py --output-dir ../pkueeg_checks/bids --validator bids-validator-deno
```

The scripts reject report destinations inside the release. BIDS validation is
not a certification of scientific reproducibility.

Publishing and download links
-----------------------------
See docs/PUBLISHING.md and docs/GITHUB_README.md. Public dataset links must use the actual OpenNeuro URL/DOI after publication.
