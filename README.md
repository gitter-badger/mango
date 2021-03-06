#mango
A set of genomic visualization tools built on top of the [ADAM](https://github.com/bigdatagenomics/adam) genomics processing engine. Apache 2 licensed.

mango visualizes reads, variants, and features using [D3](http://d3js.org/).

![Overall View](https://raw.github.com/bigdatagenomics/mango/master/images/overall.png)

![Frequency View](https://raw.github.com/bigdatagenomics/mango/master/images/frequency.png)
# Getting Started

## Installation
You will need to have [Maven](http://maven.apache.org/) installed in order to build mango.

> **Note:** The default configuration is for Hadoop 2.2.0. If building against a different
> version of Hadoop, please edit the build configuration in the `<properties>` section of
> the `pom.xml` file.

```
$ git clone https://github.com/bigdatagenomics/mango.git 
$ cd mango
$ mvn clean package -DskipTests
```
## Running mango
mango is packaged via [appassembler](http://mojo.codehaus.org/appassembler/appassembler-maven-plugin/) and includes all necessary dependencies.

Run the mango-submit script as follows:
```
bin/mango-submit REFERENCE_FILE.fa -read_file READS_FILE.bam -ref_name REFERENCE NAME -var_file VARIANTS_FILE.vcf -feat_file FEATURES_FILE.bed
```
For help launching the script, run `bin/mango-submit -h`
````
$ bin/mango-submit -h
Spark assembly has been built with Hive, including Datanucleus jars on classpath
 reference                                                       : The reference file to view, required
 -feat_file VAL                                                  : The feature file to view
 -h (-help, --help, -?)                                          : Print help
 -parquet_block_size N                                           : Parquet block size (default = 128mb)
 -parquet_compression_codec [UNCOMPRESSED | SNAPPY | GZIP | LZO] : Parquet compression codec
 -parquet_disable_dictionary                                     : Disable dictionary encoding
 -parquet_logging_level VAL                                      : Parquet logging level (default = severe)
 -parquet_page_size N                                            : Parquet page size (default = 1mb)
 -port N                                                         : The port to bind to for visualization. The default is 8080.
 -print_metrics                                                  : Print metrics to the log on completion
 -read_file VAL                                                  : The reads file to view
 -ref_name VAL                                                   : The name of the reference we're looking at
 -var_file VAL                                                   : The variants file to view
 ````
 Now view the mango genomics browser at `localhost:8080` or the port specified:
```
View the visualization at: 8080
Frequency visualization at: /freq
Overlapping reads visualization at: /reads
Variant visualization at: /variants
Feature visualization at /features
Overall visualization at: /overall
```
