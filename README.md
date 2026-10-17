# detector_drop

Encrypted drop (7-Zip AES-256, password held out of band). Updated 2026-10-17 11:53. Code dea168b, default bundle v9_40k_448_strict.

| file | MB | role |
|---|---|---|
| CANDIDATES.txt | 0 |  |
| code.7z | 5 | code + configs + docs |
| MODEL_ID.txt | 0 |  |
| model_v6_40k_448_edgetype_strict.7z.001 | 90 | candidate -> models/v6_40k_448_edgetype_strict/ |
| model_v6_40k_448_edgetype_strict.7z.002 | 90 | candidate -> models/v6_40k_448_edgetype_strict/ |
| model_v6_40k_448_edgetype_strict.7z.003 | 51.8 | candidate -> models/v6_40k_448_edgetype_strict/ |
| model_v9_40k_448_strict.7z.001 | 90 | default -> models/default/ |
| model_v9_40k_448_strict.7z.002 | 90 | default -> models/default/ |
| model_v9_40k_448_strict.7z.003 | 51.6 | default -> models/default/ |

Download (no login): `https://github.com/KwangSik-Kim/detector_drop/raw/main/<file>`  - every file listed above plus SHA256SUMS.txt.

Receive:
```
certutil -hashfile <file> SHA256        (compare with SHA256SUMS.txt)
7z x -p<password> code.7z -o<dir>
7z x -p<password> model_<name>.7z.001 -o<dir>      (volumes .002.. must sit next to .001; repeat per model_* set)
```
Then follow `<dir>/detector_judge/README_DEPLOY.md` and `docs/run_manual.md`.

Candidate bundles (not the default): v6_40k_448_edgetype_strict. Each extracts to `detector_judge/models/<name>/`;
select one with `python -m detector.cli judge <images> --model models/<name>`. The default (`models/default`) stays as is.

Backbone weights are public and not included: put `dinov2_vitb14_reg4_pretrain.pth` into `detector_judge/weights/`.
  URL https://dl.fbaipublicfiles.com/dinov2/dinov2_vitb14/dinov2_vitb14_reg4_pretrain.pth
  SHA-256 73182a088cf94833c94b1666d1c99e02fe87e2007bff57b564fb6206e25dba71  (346393545 bytes)
