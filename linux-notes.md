# Linux Revision Sheet — Bioinformatics / NGS Commands

## Day 4 Notes — Linux for Bioinformatics & NGS


# Objective

Learn Linux commands commonly used in:

* FASTQ processing
* RNA-seq workflows
* NGS pipelines
* File handling
* Automation
* Text processing
* Pipeline debugging


# 1. Navigation & File Management

These commands are used to organize sequencing projects and move across workflow directories.

| Command    | Function                  | Example                      | Bioinformatics Use       |
| ---------- | ------------------------- | ---------------------------- | ------------------------ |
| `pwd`      | Show current directory    | `pwd`                        | Verify working directory |
| `ls`       | List files                | `ls`                         | Inspect datasets         |
| `ls -lh`   | Human-readable file sizes | `ls -lh`                     | FASTQ size check         |
| `cd`       | Change directory          | `cd raw/`                    | Navigate workflows       |
| `mkdir`    | Create folder             | `mkdir qc`                   | Build pipelines          |
| `mkdir -p` | Create nested folders     | `mkdir -p results/qc`        | Project setup            |
| `cp`       | Copy files                | `cp sample.fastq qc/`        | Backups                  |
| `mv`       | Move/rename               | `mv raw.fastq sample1.fastq` | Organizing               |
| `rm`       | Delete files              | `rm temp.txt`                | Cleanup                  |
| `find`     | Locate files              | `find . -name "*.fastq"`     | Search outputs           |
| `tree`     | View structure            | `tree`                       | Project visualization    |


# 2. File Inspection

Inspect files before analysis.

| Command  | Function           | Example                |
| -------- | ------------------ | ---------------------- |
| `file`   | Detect file type   | `file sample.fastq.gz` |
| `head`   | Show first lines   | `head sample.fastq`    |
| `tail`   | Show last lines    | `tail log.txt`         |
| `cat`    | Display file       | `cat counts.txt`       |
| `less`   | Scroll large files | `less sample.fastq`    |
| `wc -l`  | Count lines        | `wc -l sample.fastq`   |
| `du -sh` | File sizes         | `du -sh raw/*`         |
| `stat`   | File metadata      | `stat sample.fastq`    |



# 3. Compression Commands

Large sequencing files are usually compressed.

| Command     | Function        | Example                           |
| ----------- | --------------- | --------------------------------- |
| `gzip`      | Compress        | `gzip sample.fastq`               |
| `gunzip`    | Decompress      | `gunzip sample.fastq.gz`          |
| `zcat`      | Read gz files   | `zcat sample.fastq.gz \| head`    |
| `tar -xvf`  | Extract archive | `tar -xvf data.tar.gz`            |
| `tar -czvf` | Create archive  | `tar -czvf backup.tar.gz folder/` |


# 4. Text Processing (Critical for NGS)

These commands are heavily used for FASTQ, metadata, counts, and annotations.

| Command | Function           | Example                   | Use           |
| ------- | ------------------ | ------------------------- | ------------- |
| `grep`  | Search text        | `grep "^@" sample.fastq`  | FASTQ headers |
| `cut`   | Extract fields     | `cut -d "," -f1 file.csv` | IDs           |
| `sort`  | Sort output        | `sort genes.txt`          | QC            |
| `uniq`  | Unique entries     | `uniq genes.txt`          | Deduplication |
| `tr`    | Replace characters | `tr " " "_"`              | Cleanup       |
| `sed`   | Stream editing     | `sed 's/A/T/g'`           | Renaming      |
| `awk`   | Column processing  | `awk '{print $1}'`        | Parsing       |
| `paste` | Merge columns      | `paste a.txt b.txt`       | Tables        |
| `join`  | Merge files        | `join file1 file2`        | Annotation    |



# 5. Pipes & Redirection

Pipeline logic is heavily used in bioinformatics.

| Symbol | Meaning                     |
| ------ | --------------------------- |
| `\|`   | Send output to next command |
| `>`    | Overwrite file              |
| `>>`   | Append file                 |
| `<`    | Input redirection           |
| `tee`  | Save + display              |

Example:

bash id="h0f3kj"
grep "^@" sample.fastq | wc -l




# 6. FASTQ-Specific Commands

## Count Total Lines
bash id="qv3hvc"
wc -l sample.fastq




## Count Reads

FASTQ Rule:

text id="gq0i44"
4 lines = 1 read


Uncompressed:

bash id="zivdb9"
expr $(wc -l < sample.fastq) / 4


Compressed:
bash id="6xiklm"
expr $(zcat sample.fastq.gz | wc -l) / 4


## Print Headers

bash id="8lc5ih"
grep "^@" sample.fastq


## View Compressed File

bash id="n1dw4d"
zcat sample.fastq.gz | head


# 7. Logging & Output Management

Create logs for reproducibility.

Overwrite:

bash id="n5c7zq"
ls raw > logs/raw_summary.txt


Append:

bash id="q0ywdv"
du -sh raw/* >> logs/raw_summary.txt


View:

bash id="g5qh7w"
cat logs/raw_summary.txt

# 8. Permissions & Scripts

| Command              | Purpose         |
| -------------------- | --------------- |
| `chmod +x script.sh` | Make executable |
| `./script.sh`        | Run script      |
| `which`              | Find tool path  |
| `history`            | Command history |


# 9. Resource Monitoring

| Command   | Purpose           |
| --------- | ----------------- |
| `top`     | Running processes |
| `htop`    | Process viewer    |
| `free -h` | RAM usage         |
| `df -h`   | Disk usage        |
| `nproc`   | CPU count         |


# 10. Bioinformatics Tools (Future Integration)

| Tool          | Purpose                 |
| ------------- | ----------------------- |
| FastQC        | Quality control         |
| MultiQC       | Aggregate QC            |
| fastp         | Preprocessing           |
| cutadapt      | Adapter trimming        |
| bwa           | Alignment               |
| STAR          | RNA-seq alignment       |
| samtools      | BAM processing          |
| bcftools      | Variant analysis        |
| bedtools      | Genomic intervals       |
| featureCounts | Count matrix generation |


# Workflow Context

text id="m6bxg0"
FASTQ
 ↓
QC
 ↓
Trimming
 ↓
Alignment
 ↓
Counts
 ↓
Statistics
 ↓
Visualization

# Current Skills Completed

✓ Linux navigation
✓ Directory management
✓ FASTQ inspection
✓ Compression handling
✓ Redirection and logs
✓ Read counting
✓ Text processing basics
✓ Project organization


# Next Linux Learning Path

text id="gd16iq"
grep / cut
      ↓
awk
      ↓
sed
      ↓
bash scripting
      ↓
FASTQ parsing
      ↓
samtools
      ↓
real pipelines

