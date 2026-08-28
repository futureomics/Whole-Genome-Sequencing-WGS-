# 🧬 Whole Genome Sequencing (WGS)  

A beginner-friendly **Whole Genome Sequencing (WGS) workflow** demonstrating how sequencing reads can be generated, aligned to a reference genome, processed, and analyzed for genomic variants.

This project uses ***E. coli*** as a small reference genome so that the complete workflow can be demonstrated efficiently without requiring large real-world FASTQ datasets.

## 📌 Workflow

```text
Reference Genome
       ↓
Simulated FASTQ Reads
       ↓
Read Alignment — BWA
       ↓
SAM → BAM Conversion
       ↓
BAM Sorting & Indexing
       ↓
Variant Calling — bcftools
       ↓
VCF File
       ↓
Variant Counting
       ↓
SNP / INDEL Classification
       ↓
Visualization
```

## 🔬 What This Project Demonstrates

The notebook covers the following steps:

1. Install required bioinformatics tools
2. Download an ***E. coli* reference genome**
3. Simulate sequencing reads in FASTQ format
4. Introduce mutations into simulated reads
5. Align reads against the reference genome using **BWA**
6. Convert SAM to BAM using **SAMtools**
7. Sort and index BAM files
8. Call variants using **bcftools**
9. Count detected variants
10. Classify variants into **SNPs and INDELs**
11. Visualize SNP vs INDEL counts

## 🛠️ Tools & Technologies

| Tool         | Purpose                             |
| ------------ | ----------------------------------- |
| Python       | Data processing and read simulation |
| Biopython    | FASTA/reference genome handling     |
| Pandas       | Variant data analysis               |
| NumPy        | Numerical operations                |
| Matplotlib   | Visualization                       |
| BWA          | Sequence alignment                  |
| SAMtools     | BAM processing                      |
| bcftools     | Variant calling                     |
| NCBI         | Reference genome source             |
| Google Colab | Cloud-based execution               |

## 📂 Project Structure

```text
.
├── Whole_Genome_Sequencing_(WGS)_demo.ipynb
└── README.md
```

## 🧪 Dataset

The workflow downloads the ***E. coli* K-12 reference genome** from NCBI and saves it locally as:

```text
ecoli_ref.fasta
```

Instead of downloading a large sequencing dataset, the notebook generates simulated reads from the reference sequence.

The simulated reads are:

* **Read length:** 150 bp
* **Number of reads:** 6,000
* **Mutation rate:** 1%

The resulting sequencing file is:

```text
reads.fastq
```

## 🧬 Alignment

The simulated FASTQ reads are aligned to the reference genome using **BWA-MEM**:

```bash
bwa index ecoli_ref.fasta
bwa mem ecoli_ref.fasta reads.fastq > aln.sam
```

The notebook successfully processes **6,000 reads / 900,000 bp** during alignment.

## 🧫 BAM Processing

The SAM alignment file is converted to BAM, sorted, and indexed:

```bash
samtools view -Sb aln.sam > aln.bam
samtools sort aln.bam -o aln.sorted.bam
samtools index aln.sorted.bam
```

## 🔎 Variant Calling

Variants are called using **bcftools**:

```bash
bcftools mpileup -f ecoli_ref.fasta aln.sorted.bam | \
bcftools call -mv -Ov -o variants.vcf
```

The resulting variants are stored in:

```text
variants.vcf
```

## 📊 Results

The notebook reports:

```text
Total variants detected: 6407
```

Variant classification gives:

| Variant Type |     Count |
| ------------ | --------: |
| SNP          |     6,403 |
| INDEL        |         4 |
| **Total**    | **6,407** |

These values are the outputs recorded in the uploaded notebook.

> **Note:** These results come from simulated reads and should be treated as a demonstration of the analysis workflow, not as biological conclusions from a real WGS experiment.

## ▶️ How to Run

### Option 1 — Google Colab

Upload the notebook to Google Colab and execute the cells sequentially.

### Option 2 — Local Jupyter

Install the required packages:

```bash
pip install biopython pandas numpy matplotlib
```

Install the command-line tools:

```bash
sudo apt-get install bwa samtools bcftools
```

Then launch:

```bash
jupyter notebook
```

and open:

```text
Whole_Genome_Sequencing_(WGS)_demo.ipynb
```

## 🎥 Future Omics — Bioinformatics Made Easy

For more bioinformatics, genomics, and omics tutorials:

📺 **Future Omics — Bioinformatics Made Easy**
📺 Future Omics — Bioinformatics Made Easy https://www.youtube.com/@Bioinformatics_Made_Easy?sub_confirmation=1 

The channel focuses on simplified bioinformatics and omics tutorials for students, researchers, and life-science learners.

## 📚 Learning Outcomes

After completing this project, you should understand the basic computational flow of a WGS experiment:

* FASTA vs FASTQ
* Reference genome
* Sequencing reads
* Read alignment
* SAM/BAM files
* BAM sorting and indexing
* Variant calling
* VCF files
* SNPs vs INDELs
* Basic variant visualization

## 🚀 Future Improvements

This demonstration can be extended into a more realistic WGS pipeline by adding:

* FastQC / MultiQC quality control
* Adapter and quality trimming
* Real FASTQ datasets
* Read-depth and coverage analysis
* GATK-based variant calling
* Variant annotation using **VEP** or **ANNOVAR**
* Variant filtering and prioritization
* Genome browser visualization
* Nextflow workflow automation
* Docker/Singularity containerization
* Cloud-based WGS analysis

## 👩‍🔬 Applications of WGS

Whole Genome Sequencing can be applied to areas including:

* Clinical genomics
* Rare disease research
* Cancer genomics
* Population genomics
* Microbial genomics
* Pathogen surveillance
* Evolutionary genomics
* Precision medicine

## ⭐ Acknowledgement

This repository is intended as an educational demonstration of a WGS bioinformatics workflow.

If you find this project useful, consider ⭐ starring the repository and following **Future Omics — Bioinformatics Made Easy** for more bioinformatics tutorials.

---

### 🔗 Resources

* 🧬 **Future Omics YouTube:** https://www.youtube.com/@Bioinformatics_Made_Easy?sub_confirmation=1 
* 🧪 **NCBI Genome Database:** https://www.ncbi.nlm.nih.gov/genome/
* 🧬 **BWA:** https://github.com/lh3/bwa
* 🧫 **SAMtools:** https://github.com/samtools/samtools
* 🔬 **BCFtools:** https://github.com/samtools/bcftools
