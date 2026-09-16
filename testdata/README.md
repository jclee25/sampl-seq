# Example dataset

Place `test_R1.fastq.gz` in `testdata/` (sample ID: `test`).
The FASTQ is excluded from version control. The release download link and
validated reference outputs are not yet available.

- Size: 548,784,345 bytes
- SHA-256:

```text
ac13943c59b4f96d41164f1132e2697338175e155e9aff373bdc07884316e489
```

## Prepare and run

Complete the [installation](../README.md#installation), then run these commands
from the repository root (`sampl-seq/`):

```bash
ANALYSIS_ID=testdata
mkdir -p "input/${ANALYSIS_ID}" "config/output/${ANALYSIS_ID}"
cp -n config/parameters.env.example \
  "config/output/${ANALYSIS_ID}/parameters.env"
ln -s ../../testdata/test_R1.fastq.gz \
  "input/${ANALYSIS_ID}/test_R1.fastq.gz"
```

The symlink lets the pipeline read the FASTQ without copying it out of `testdata/`.
Existing inputs and configurations are not overwritten; skip `ln -s` if already linked.
Edit `config/output/testdata/parameters.env` to set `TAXONOMY_DB=` and check
the remaining settings. `output/testdata/` must be absent or empty.

Keep `ANALYSIS_ID=testdata` and follow the [01–05 execution commands](../README.md#run-the-pipeline)
in order, inspecting each step and stopping if it fails. Results are written
under `output/testdata/`.
If reducing CPU cores, update both `THREADS` in the configuration and the
core-count argument in script 05.
