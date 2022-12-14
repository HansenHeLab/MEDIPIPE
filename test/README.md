## Input configfile specification
> **IMPORTANT**: READ THROUGH THE GUIDE INFORMATION IN THE TEMPLATES TO MAKE CORRECT MANIFEST TALBES AND CONFIG FILE.

### Step 1: Prepare reference, samples FASTQ and aggregation files
1) You can download reference genome, pre-build BWA index and annotated regions (e.g., blacklist) from ENCODE for hg38 and hg19 using the scripts in .assets/Reference. The reference manifest table hg38/hg19.tsv will be generated accordingly. Currently, the ENCODE black list and bwa index are mandatory for the manifest file, which means you can also create it by yourself based on `.Reference/hg38_template.tsv` or example below:

|	genome_name   |     hg38	 |
|---------------|------------|
| bwa_index	    |  /path/to/bwa/index |
| blacklist     |  /path/to/blacklist/regions  |


2) The samples's sequence data table template. Note:Prepare the table for single-end and paired-end samples separately and use exactly same table `header`, if there are multiple lanes, use comma to separate the list.

|	sample_id   |     R1	     |  R2(p.r.n.)|
|-------------|--------------|------------|
|  A	|  full/path/to/A_L001_R1.fq.gz |                              |
|  B	|  full/path/to/B_L001_R1.fq.gz | full/path/to/B_L001_R2.fq.gz |
|  C  |  path/C_L001_R1.fq.gz,path/C_L002_R1.fq.gz | path/C_L001_R2.fq.gz,path/C_L002_R2.fq.gz  |

3) The samples aggregation template. groups can refer to different batches or cancer subtypes, etc.

|	sample_id   |     group	   |
|-------------|--------------|
|  A	|  G1 |
|  B	|  G1 |
|  C  |  G2 |
|  D  |  G2 |

### Step 2: Specify input configuration file by following the instructions
A config YAML file specifies all PATHs of input files and parameters that are necessary for successfully running this pipeline. This includes a specification of the path to the genome reference files. Please make sure to specify absolute paths rather than relative paths in your config files. More detailed instructions can be found at the [config_template](./test/config_template.yaml)


## Test dataset

The current toy cfMeDIP-seq data is randomly derived from the two BACs ([F19K16](https://www.arabidopsis.org/servlets/TairObject?type=assembly_unit&id=362) and [F24B22](https://www.arabidopsis.org/servlet/TairObject?type=AssemblyUnit&name=F24B22)) Arabidopsis by [Min Han](https://github.com/mhanbioinfo/make_toy_fastqs)

`Reference/`: Genome reference and BWA index (Athaliana.BAC.F19K16.F24B22 )   
`Fastq/` : Randomly generated paired-end FastQ reads   
