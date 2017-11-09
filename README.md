## Intel Optimized GATK-3 Germline SNPs and Indels Variant Calling Workflow. 

### WORKFLOWS AND JSONS
This repository contains a few different files - each tuned for certain requirements. 

├── 2T_Exome_NonDocker.json &rarr; Throughput JSON file \
├── 56T_Exome_NonDocker.json &rarr; Latency JSON file \
├── Exome_Workflow.wdl &rarr; WDL optimized for on-prem

For the Exome_Workflow.wdl file, modify [Line 568](https://github.com/gatk-workflows/intel-gatk3-germline-snps-indels/blob/master/Exome_Workflow.wdl#L568) to the path where datasets reside in your cluster. 

In the JSON files, modify the paths to the datasets and tools where they reside in your cluster.

### DATASETS
Contact Intel/Broad for access to the WES data needed for this workflow.

### TOOLS
For on-prem, the workflow uses non-dockerized tools. To keep up with the exact 
versions released by Broad for their best practices workflow, we download the 
tools from the docker image to our shared file system. 

Run the command: 
```
docker run -v /path/to/shared_filesystem:/path/to/shared_filesystem -it broadinstitute/genomes-in-the-cloud:2.2.5-1486412288 /bin/bash
```

This command will pull the docker image (if it is not already there locally), 
and put you within the container from where you can copy the tools needed for 
the workflow. 

```
root@54754360159e:/usr/gitc# cp /usr/local/bin/samtools bwa picard.jar /path/to/shared_filesystem
root@54754360159e:/usr/gitc# exit
```

In addition to above, this workflow uses the latest optimized GATK 3.8-1 jar with 
optimizations which can be obtained from [GATK website](https://software.broadinstitute.org/gatk/download/). 


