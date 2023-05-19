# Documentation for Flomics *in silico* QC metrics 

## Adding new metrics: consistency guidelines

- Metric names should start with a lowercase letter
- Use '`_`' as token separator in metric names (*e.g.* `count_spliced_reads`)
- Metrics representing a **fraction**:
    - should be represented as decimals, comprised between 0 and 1 (not between 0 and 100)
    - should have their name start with the '`frac_`' string
- Metrics representing a **count** should have their name start with the '`count_`'
- Always specify in the documentation what range of values a metric is supposed to vary within, unless obvious


## Availability

Read the manual here: 

https://flomicsrnaseq-flomicsqc-manual.readthedocs.io

