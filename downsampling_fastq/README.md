# downsampling_fastq

Normally if downsampling you'd want to take a random sample of the sequences present in your *.fastq file. However, we ran into an issue where the R sequences had been concatenated on to the end of the F sequences. We still wanted to downsample, but that meant we had to be "regular" about taking sequences. We wrote the attached scripts in order to take every fourth sequence (and title and associated quality data etc etc: basically looking to shave 3/4 off the original fastq file size).

To run this script, you need to export the following arguments:
```
export filename=/panfs/pfs.local/scratch/bi/trunks18/For_Cluster/reads/full_bemHap/bemHap1-pe100-reads.fq

export perc_to_sample=0.25
```

After exporting your variables making sure that downsampling_fastq.sh and downsampling_fastq.R are in your working directory, you can execute the code by:
```
bash downsampling_fastq.sh
```
Be aware you'll need at least as much memory available as the size of the original fastq file (likely more, but I didn't really test how memory efficient it was).

If you get the following message:
"You will need to split your fastq file in two to proceed as it has too many lines to be read in by R"

You'll need to use split_downsampling_fastq.sh instead of downsampling_fastq.sh. The Rscript should remain the same.

## Version history
This code was used for: Gustafson, G.T., Alexander, A., Sproul, J.S., Pflug, J.M., Maddison, D.R. and Short, A.E., 2019. Ultraconserved element (UCE) probe set design: Base genome and initial design parameters critical for optimization. Ecology and Evolution.

This script wouldn't be possible without:  
R: R Core Team. 2015. R: A language and environment for statistical computing. URL http://www.R-project.org/. R Foundation for Statistical Computing, Vienna, Austria. https://www.r-project.org/  

Matt Dowle and Arun Srinivasan data.table: Extension of `data.frame`. R package version 1.12.0. https://CRAN.R-project.org/package=data.table
