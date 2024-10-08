# T-rich-DNA_NT analysis
This section provides customized code for the analysis presented in the paper: Molecular Basis of an Adenine-Rich Template DNA-Induced Spontaneous Transcription Termination.

## Software/package
1. Python -v3.9.12 
2. argparse -v3.2

## Step 1: Calculate the T Enrichment Score
To calculate the T enrichment score, use base_enrichment.py with the following command:
```
python base_enrichment.py --genome {your_genome.fa} --output {your_output_file_name} --window {default=10, your expected window size} --base {default=T, base to calculate}
```
This command generates a BED file containing the base enrichment information. You can convert the resulting BED file to a BigWig file for visualization using bedGraphToBigWig.

## Step 2: base-enriched boundaries Boundaries Detection
To detect base-enriched boundaries within specific regions, use boundary_detection.py alongside the BED file generated by base_enrichment.py:
```
python boundary_detection.py --region {your_region_in_BED_format} --output {your_output_file_name} --ref {BED file generated by base_enrichment.py} --window {default=30, expected window size for boundaries} --filter {default=10, lowest score to consider as enrichment}
```
This step generates a BED file containing an additional column that marks whether a region has base-enriched boundaries (True/False).
