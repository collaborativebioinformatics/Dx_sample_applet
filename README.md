# Dx_sample_applet
## This is a template repo for DNAnexus community applets

### Function/Overview

### Inputs

### Configuration

### Outputs

### Citations

### Dependencies

### Example

---

## Example Documentation

### Function/Overview

Vcfanno-runner is a lightweight DNAnexus app that runs the open-source vcfanno executable (https://github.com/brentp/vcfanno) on DNAnexus. Vcfanno adds annotations to query VCFs as INFO tags based on indexed annotation sources like VCFs, BEDs, and other file formats

### Inputs

### Configuration

The DNAnexus vcfanno configuration TOML is like the native vcfanno TOML, except
the annotation table's `file` key points to DNAnexus file URIs instead of local
filesystem paths (see https://github.com/brentp/vcfanno#usage for more details
about the native vcfanno TOML). The DNAnexus TOMLs enable users to leverage key
features of DNAnexus (e.g., reproducibility, traceability) while running
vcfanno in a natural way (i.e., users pass TOMLs to vcfanno-runner like they
would to vcfanno)

Vcfanno-runner compiles the native TOML based on the DNAnexus TOML and sets up
the runtime environment for vcfanno. To do so, it retrieves the annotation
sources referenced in the DNAnexus TOML, optimistically retrieving the
corresponding index files, and puts everything at select paths. For example

```yaml
# DNAnexus TOML
[[annotation]]
file = "project-xxxx:file-xxxx"
...
```

would compile to

```yaml
# Native TOML
[[annotation]]
file = "/path/to/my.bed.gz"
...
```

and the runtime environment would look like

```bash
/
|-- path
    |-- to
        |-- my.bed.gz
        |-- my.bed.gz.tbi
```
### Outputs

### Citations

### Dependencies

### Example
