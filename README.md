# nf-benchmark

# nf-benchmark: Documentation

The nf-benchmark documentation is split into the following files:

1. [Installation](https://nf-co.re/usage/installation)
2. Pipeline configuration
    * [Local installation](https://nf-co.re/usage/local_installation)
    * [Adding your own system config](https://nf-co.re/usage/adding_own_config)
    * [Reference genomes](https://nf-co.re/usage/reference_genomes)
3. [Running the pipeline](usage.md)
4. [Output and how to interpret the results](output.md)
5. [Troubleshooting](https://nf-co.re/usage/troubleshooting)

## Quick start

1. Install [`nextflow`](https://www.nextflow.io/docs/latest/getstarted.html#installation)

2. Install either [`Docker`](https://docs.docker.com/engine/installation/) or 
[`Singularity`](https://www.sylabs.io/guides/3.0/user-guide/) to use the sandboxes images containing the software used 
by the pipeline.

3. Clone the repository:

```bash
git clone https://github.com/cbcrg/nf-benchmark
```
4. Run nf-benchmark

```bash
nextflow run main.nf --pipeline tcoffee -profile docker,test_nfb -resume
```

## Add your pipeline 

## How to run the pipeline

### From root

```bash
NXF_VER=20.04.1-edge nextflow run main.nf \
    --pipeline regressive_alignment \
    --regressive_align false \
    --align_methods CLUSTALO \
    --evaluate false \
    -profile test,docker \
    -resume
```

### From a module

#### t-coffee

```bash
nextflow run main.nf --pipeline tcoffee --skip_benchmark -resume
```

```bash
nextflow run main.nf --pipeline tcoffee --skip_benchmark -profile docker,test_nfb -ansi-log false -resume
```

#### Regressive-alignment

```bash
NXF_VER=20.04.1-edge nextflow run main.nf \
    --regressive_align true \
    --align_methods CLUSTALO \
    -profile test,docker \
    -resume
```

* 2020/07/28 

```bash
NXF_VER=20.04.1-edge nextflow run main.nf \
    --pipeline regressive_alignment_new  \
    --regressive_align false \
    --align_methods CLUSTALO \
    --evaluate false \
    -profile test,docker
```

#### Directly run regressive alignment pipeline

```bash
NXF_VER=20.04.1-edge nextflow run main.nf \
    --regressive_align true \
    --align_methods CLUSTALO \
    -profile test,docker \
    -resume
```

#### With makefile

```bash
make regressive | nextflow run main.nf \
    --pipeline regressive_alignment \
    --skip_benchmark \
    -profile docker,test_nfb \
    -ansi-log false \
    -resume
```

## declare workflow on main as pipeline  

```bash
NXF_VER=20.04.1-edge nextflow run main.nf --regressive_align false --align_methods "CLUSTALO" --evaluate false -profile test,docker -resume
```

## Points to add to the documentation

### Structure

#### Modules/pipelines/

### Modules/benchmarks

### Modules/assests

### Include yml file

### Include a test config

If you want to use the test_nfb you should include a configuration file in pipelines/your_pipeline/conf/test_nfb.config
Otherwise, you can use your own test file using -c option see 

### Params:

--params.pipeline 

--params.path_to_pipelines

--params.path_to_benchmarks

## Tables description:

### methods2benchmark:

The **methods2benchmark.csv** table contains the relationship between the pipeline method, its data input output and 
finally the benchmark, it contains the following fields:

* edam_operation
* edam_input_data
* edam_input_format
* edam_output_data 
* edam_output_format
* benchmarker

The input and output data of benchmarkers can be found in **dataFormat2benchmark.csv**. The fields of the table are:

* benchmarker
* edam_operation
* edam_test_data
* edam_test_format
* edam_ref_data
* edam_ref_format
   