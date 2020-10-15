Software requirement:
-----------------
1. Python 3.6 or higher (https://www.python.org/)
2. Tensorflow package (Initial experiment uses version 1.14) (https://www.tensorflow.org/)
3. Biopython package (https://biopython.org/)
4. Numpy package (http://www.numpy.org/)
5. C++ (http://www.cplusplus.com/)

Data Preparation:
-----------------
Check config file format (configure to your setting)

* config file included in the package is configured to sample set using only CPU
* the aligned paired-end reads file (SAM format) and corresponding reference file (FASTA format) are required for haplotype assembly
* the order of rows in config file matters and the space + colon + space (" : ") to seperate variable name and value is required

Config file example: 
filename of reference sequence (FASTA) : CAEC_haplo.fasta  
filname of the aligned reads (sam format) : CAEC_haplo.sam
SNP_thres (0.5 / ploidy) : 0.125
reconstruction_start : 1
reconstruction_stop : 5000
min_mapping_qual : 60
min_read_length : 70
max_insert_length : 3000
characteristic zone name : CAEC_haplo
K (ploidy) : 4
Number of experiments : 10
Which GPU to use (set to -1 if only use CPU; otherwise set to 0, 1, 2 or 3 ... if multiple GPUs are available; check instructions for details) : 1
MEC improvement threshold(This is used for viral quasispecies reconstruction) : 0.09

1. filename of reference sequence (FASTA) represents the name of the reference genome in .fasta or .fa format.
2. filname of the aligned reads (sam format) represents the name of the aligned paired-end reads file in .sam format.
3. SNP_thres represents the threshold for SNP calling. The lower it is, the more nucleotide positions would be considered as SNPs. (it's set to 0.5 / ploidy in initial experiments)
4. reconstruction_start represents the index in reference genome that is corresponding to the starting position of the genome region of interest (1 corresponds to the first nucleotide of the reference genome).
5. reconstruction_stop represents the index in reference genome that is corresponding to the ending position of the genome region of interest.
6. min_mapping_qual represents minimum read quality score (reads with score lower than it would be discarded).
7. min_read_length represents the minimum read length (reads shorter than it would be discarded).
8. max_insert_length represents the maximum insert length of reads (reads with insert longer than it would be discarded)
9. characteristic zone name can be set to any name of your choice.
10. K (ploidy) represents the ploidy.
11. Number of experiments represents the number of experiments for which CAECseq would be implemented and the reconstructed haplotypes corresponding to the lowest MEC score would be the stored in haplotypes.txt file.  
12. Which GPU to use represents the GPU you want to use. Use (from tensorflow.python.client import device_lib device_lib.list_local_devices()) to check the index of GPUs that are available
13. MEC improvement threshold(This is used for viral quasispecies reconstruction) : 0.09

Running CAECseq:
-----------------
1. First set up config file.
2. Command : 
    (1) ./ExtractMatrix config
    (2) python CAEC_viral.py config
    Output : haplotypes.txt

**Alignment can be done via BWA MEM (http://bio-bwa.sourceforge.net/bwa.shtml) to generate the SAM file from FASTQ (reads) and FASTA (reference genome) files. SAM file can be sorted using "samtools sort".**