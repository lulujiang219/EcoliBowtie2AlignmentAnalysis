# **EcoliBowtie2AlignmentAnalysis**
## Introduction
This project provides an efficient and user-friendly pipeline to analyze E. coli sequencing data. Leveraging the power of Bowtie2, SAMtools, and BCFtools, it aims to offer researchers and bioinformatics enthusiasts a streamlined method to align reads and detect genomic variants.

## Features:
Index building from the E. coli genome using bowtie2-build.
Efficient alignment of sequencing reads with Bowtie2.
Generation of BAM and sorted BAM files with SAMtools.
Variant calling with BCFtools to identify indels and other genomic variants.
## Prerequisites:
[Bowtie2](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml)
[SAMtools](http://www.htslib.org/)
[BCFtools](http://www.htslib.org/doc/bcftools.html)

## **Usage:**
### 1. Clone the Repository:

```
git clone https://github.com/YourUsername/EcoliBowtie2AlignmentAnalysis.git
cd EcoliBowtie2AlignmentAnalysis
```
### 2. Index Building:

`bowtie2-build ecolicompletegenome.fasta ecoli_index`
### 3. Run the Alignment:

`bowtie2 -x ecoli_index -f query_seqs.fasta -S output.sam`
### 4. Convert SAM to BAM and Sort:

```
samtools view -bS output.sam > output.bam
samtools sort output.bam -o output_sorted.bam
```
### 5. Variant Calling:

`bcftools mpileup -Ou -f ecolicompletegenome.fasta output_sorted.bam | bcftools call -Ov -mv -o variants.vcf`
Results:
After executing the pipeline, you'll obtain a VCF file (variants.vcf) containing potential genomic variants in the analyzed reads.

## Contributing:
Feel free to fork the project, make your improvements, and submit a pull request. Your contributions are always welcome!

## License:
This project is licensed under the MIT License. Refer to the LICENSE file for more details.

## Acknowledgements:
Thanks to the BF527 course for inspiring this project and providing the datasets.
