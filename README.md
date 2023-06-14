# Documentation for Flomics *in silico* QC metrics 

## Adding new metrics: consistency guidelines

Apply the following rules in **decreasing order of priority**:

- Names should include only alphanumeric characters, and no spaces
- Use '`_`' as token separator in metric names (*e.g.* `count_spliced_reads`)
- Metrics pulled from third-party software should start with the name of the metric as provided by MultiQC and end with the name of the software (shortened if needed) (*e.g.* `per_base_sequence_quality_fastqc`)
- Metric names should start with a lowercase letter
- Metrics representing a **count**/**average**/**median** should have their name start with '`count_`'/'`avg`'/'`med`', respectively
- Metrics representing a **fraction**:
    - should be represented as decimals, comprised between 0 and 1 (not between 0 and 100)
    - should have their name start with '`frac_`'
- Always specify in the documentation what range of values a metric is supposed to vary within, unless very obvious

## Availability

Read the manual here: 

https://flomicsrnaseq-flomicsqc-manual.readthedocs.io

