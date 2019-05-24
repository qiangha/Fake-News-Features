# In this file, I show the preprocessing steps

I first create the cluster (see cluster.md on how to create a cluster), upload all files to the bucket and unzip the files
 (uploading files using gsutil cp command)
 e.g. gsutil a.txt gs://good-bucket
 
 (unzipping file using gunzip command)
 e.g. gunzip a.json.gz
 
 For example, uploading all gz files about hillary and then unzip them would be:
gsutil cp *.gz gs://good-bucket/hillary/
gunzip *.gz

