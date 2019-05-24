# this file explains how to intiate a cluster and open pyspark notebook on it

## first make bucket
gsutil mb gs://good-bucket

## then create the cluster
gcloud dataproc clusters create cluster-qiang --bucket good-bucket\
 --subnet default --bucket good-bucket --zone europe-west2-a --master-machine-type n1-standard-4 --master-boot-disk-size 500 --num-workers 2 --worker-machine-type n1-standard-4 --worker-boot-disk-size 500 --image-version 1.3-deb9 --project st446-final-project \
 --initialization-actions 'gs://dataproc-initialization-actions/jupyter/jupyter.sh' 
 
 #add different intialisation scripts if necessary
 
 #for topic_modelling use initialisation scripts
 --initialization-actions 'gs://dataproc-initialization-actions/jupyter/jupyter.sh','gs://dataproc-initialization-actions/python/pip-install.sh','gs://bucket-qiang/my-actions.sh' \
 --metadata 'PIP_PACKAGES=sklearn nltk pandas numpy'
 
 my-action.sh can be found in the helper folder
 
 #for machine_learning use intialisation scripts   no special intialisation scripts
 
 #for graph_query use intialisation scripts 
 --initialization-actions 'gs://dataproc-initialization-actions/jupyter/jupyter.sh','gs://dataproc-initialization-actions/python/pip-install.sh','gs://dataproc-initialization-actions/zookeeper/zookeeper.sh','gs://dataproc-initialization-actions/kafka/kafka.sh' \
  --metadata 'PIP_PACKAGES=sklearn nltk pandas graphframes'



 ##ssh into a virtual machine and open a pyspark notebook

export PORT=8123
export HOSTNAME=cluster-qiang-m
export ZONE="europe-west2-a"
export PROJECT="st446-final-project"

gcloud compute ssh ${HOSTNAME} \
>     --project=${PROJECT} --zone=${ZONE}  -- \
>     -D ${PORT} -N &

"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
      --proxy-server="socks5://localhost:${PORT}" \
      --user-data-dir=/tmp/${HOSTNAME}
