List of QC metrics
==========

In this document, we will find the definitions of each of the metrics of the FlomicsQC module, along with the software that produces it. If it is produced in house, we will specify how it is produced.

In house
++++++++++++++
List of metrics obtained in house with a list of scripts.

* **dataset**: name of the sample.
* **trackhub_link**: link to the trackhub of the entire run. It will contain all of the samples of the run.
* **Number_mapped_unique_molecules**: number of reads in the bam file after the UMI deduplication.
* **Percentage_unique_molecules**: percentage of unique reads. It is calculated as: number of reads in the bam file before deduplication/ number of reads in the bam file after deduplication * 100
* **uniqMappedReads**: number of uniquely mapped reads from the deduplicated bam file.
* **splicedReads**: number of spliced reads.
* **%splicedReads**: percentage of uniquely mapped reads that are spliced.
* **totalSJs**: total number of splice junctions.
* **knownSJs**: total number of known splice junctions.
* **%knownSJs**: percentage of splice junctions that are known.
* **Junction_saturation_slope**: slope of the saturation curve of the splice junctions from 95 to 100%. This shows if the number of splice junctions are saturated (deeper sequencing would not result in more splice junctions). It is calculated from the `RSeQC <https://rseqc.sourceforge.net/#junction-saturation-py>`_.
* **read_coverage_uniformity_score**: score that accounts for the coverage uniformity of the genes. It calculates the AUC of the profile generated by `Qualimap <http://qualimap.conesalab.org/doc_html/analysis.html#rna-seq-qc>`_.
* **genes_contributing_to_1%_of_reads**: number of genes that contribute to >=1% of the total library size. Calculated using the output from `Salmon <https://salmon.readthedocs.io/en/latest/>`_.
* **genes_contributing_to_5%_of_reads**: number of genes that contribute to >=5% of the total library size. Calculated using the output from `Salmon <https://salmon.readthedocs.io/en/latest/>`_.
* **genes_contributing_to_10%_of_reads**: number of genes that contribute to >=10% of the total library size. Calculated using the output from `Salmon <https://salmon.readthedocs.io/en/latest/>`_.
* **genes_contributing_to_50%_of_reads**: number of genes that contribute to >=50% of the total library size. Calculated using the output from `Salmon <https://salmon.readthedocs.io/en/latest/>`_.
* **genes_contributing_to_80%_of_reads**: number of genes that contribute to >=80% of the total library size. Calculated using the output from `Salmon <https://salmon.readthedocs.io/en/latest/>`_.
* **Reads_mapping_sense_percentage**: percentage of reads mapping to the sense strand. Calculated from the output of `RSeQC <https://rseqc.sourceforge.net/#infer-experiment-py>`_. 
* **Reads_mapping_antisense_percentage**: percentage of reads mapping to the antisense strand. Calculated from the output of `RSeQC <https://rseqc.sourceforge.net/#infer-experiment-py>`_. 
* **Reads_undetermined_strandedness_percentage**: percentage of reads where the mapping strand could not be determined. Calculated from the output of `RSeQC <https://rseqc.sourceforge.net/#infer-experiment-py>`_.
* **Ala_tRNA, Arg_tRNA, Asn_tRNA, Asp_tRNA, Cys_tRNA, Gln_tRNA, Glu_tRNA, Gly_tRNA, His_tRNA, IG_C_gene, IG_C_pseudogene, IG_D_gene, IG_J_gene, IG_J_pseudogene, IG_V_gene, IG_V_pseudogene, IG_pseudogene, Ile_tRNA, Leu_tRNA, Lys_tRNA, Met_tRNA, Mt_rRNA, Mt_tRNA, Phe_tRNA, Pro_tRNA, Pseudo_tRNA, SeC(e)_tRNA, SeC_tRNA, Ser_tRNA, Sup_tRNA, TEC, TR_C_gene, TR_D_gene, TR_J_gene, TR_J_pseudogene, TR_V_gene, TR_V_pseudogene, Thr_tRNA, Trp_tRNA, Tyr_tRNA, Undet_tRNA, Val_tRNA, lncRNA, miRNA, misc_RNA, polymorphic_pseudogene, processed_pseudogene, protein_coding, pseudogene, rRNA, rRNA_pseudogene, ribozyme, sRNA, scRNA, scaRNA, snRNA, snoRNA, spike_in, transcribed_processed_pseudogene, transcribed_unitary_pseudogene, transcribed_unprocessed_pseudogene, translated_processed_pseudogene, translated_unprocessed_pseudogene, unitary_pseudogene, unprocessed_pseudogene, vault_RNA**: gene quantification for each of the biotypes.
* **pearson_coef**: pearson coefficient of the correlation between the ERCC spike-ins quantification and their concentration.
* **spearman_coef**: spearman coefficient of the correlation between the ERCC spike-ins quantification and their concentration.
* **r_squared**: R2 of the correlation between the ERCC spike-ins quantification and their concentration.

FastQC
++++++++++++++
Quality control metrics obtained from `FastQC <https://www.bioinformatics.babraham.ac.uk/projects/fastqc/>`_. They can be pass/warn/fail depending on the quality of the sample at each metric.

* **per_base_sequence_quality**: distribution of the quality of the sample at base level. It will be **warn** if  the lower quartile for any base is less than 10, or if the median for any base is less than 25. It will be fail if the lower quartile for any base is less than 5 or if the median for any base is less than 20.
* **per_sequence_quality_scores**: distribution of the quality of the sequences at base level. It will be **warn** if the most frequently observed mean quality is below 27 (0.2% error rate). It will be **fail** if the most frequently observed mean quality is below 20 (1% error rate).
* **per_base_sequence_content**: proportion of each base at each position of the sequence. It will be **warn** if the difference between A and T, or G and C is greater than 10% in any position. It will be **fail** if the difference between A and T, or G and C is greater than 20% in any position.
* **per_sequence_gc_content**: distribution of GC content across the length of each sequence in a sample. It will be **warn** if the sum of the deviations from the normal distribution represents more than 15% of the reads. It will be **fail** if the sum of the deviations from the normal distribution represents more than 30% of the reads.
* **per_base_n_content**: distribution of N contents in any position of the sequence. It will be **warn** if any position shows an N content of >5%. It will be **fail** if any position shows an N content of >20%.
* **sequence_length_distribution**: distribution of the length of the sequences. It will be **warn** if if all sequences are not the same length. I will be **fail** if any of the sequences have zero length.
* **sequence_duplication_levels**: distribution of the duplicated sequences. It will be **warn** if non-unique sequences make up more than 20% of the total. It will be **fail** if non-unique sequences make up more than 50% of the total.
* **overrepresented_sequences**: number of overrepresented sequences. It will be **warn** if any sequence is found to represent more than 0.1% of the total. It will be **fail** if any sequence is found to represent more than 1% of the total.
* **adapter_content**: number of adapter sequences. It will be **warn** if any sequence is present in more than 5% of all reads. It will be **fail** if if any sequence is present in more than 10% of all reads.
  
Trim galore
++++++++++++++
Metrics obtained from `Trim Galore <https://www.bioinformatics.babraham.ac.uk/projects/trim_galore/>`_. Trim galore trims the adapter sequences and low-quality reads and low-quality bases of the reads. It will discard reads with less than X bases, depending on the configuration

* **Read_number**: number of reads as input for trim galore.
* **Reads_passing_trimming**: number of reads that passed the trim galore trimming step.
* **Percentage_reads_passing_trimming**: percentage of reads that pass the trimming step (Reads_passing_trimming/Read_number*100).

STAR
++++++++++++++
Metrics obtained from `STAR <https://github.com/alexdobin/STAR/blob/master/doc/STARmanual.pdf>`_.

**total_reads**: number of reads as input for STAR.
**avg_input_read_length**: average read length as input for STAR .
**number_of_uniquely_mapped_reads**:  number of reads that map uniquely in the genome.
**percentage_of_uniquely_mapped_reads**: percentage of reads that map uniquely in the genome.
**avg_mapped_read_length**: average mapped read length. 
**number_of_multimapped_reads**: number of reads that map multiple times in the genome.
**percentage_of_unmapped_too_short_reads**: number of reads don't map to the genome because the length of the mapping is too short. **Important!** It doesn't mean that the read is too short but that the part of the read that aligns to the genome is too short.
**mapped_percentage**: percentage of reads that map to the genome (number_of_uniquely_mapped_reads+number_of_multimapped_reads/total_reads)
**average_mapped_length_percentage**: ratio between the avg_input_read_length and the avg_mapped_read_length. Useful to see which is the lenght of the alignment. Calculated as (the avg_mapped_read_length/avg_input_read_length*100)

Qualimap
++++++++++++++
Metrics obtained from `Qualimap <http://qualimap.conesalab.org/doc_html/analysis.html#rna-seq-qc>`_.

**Exonic**: number of reads mapped into exonic regions.
**Intronic**: number of reads mapped into intronic regions.
**Intergenic**: number of reads mapped into intergenic regions.
**Exonic_percentage**: percentage of reads mapped into exonic regions.
**Intronic_percentage**: percentage of reads mapped into intronic regions.
**Intergenic_percentage**: percentage of reads mapped into intergenic regions.

Picard
++++++++++++++
Metrics obtained from `Picard <https://gatk.broadinstitute.org/hc/en-us/articles/360037055772-CollectInsertSizeMetrics-Picard->`_.

* **median_insert_size**: median of the insert sizes of the reads (equivalent to the RNA length).
