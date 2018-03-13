---

title: Pachyderm for NLP?
layout: default
category: cl
 
---

# My problem

I have developed quite a set up for doing machine learning and other tasks (80+ cpu cores and 150+ GB of ram combined). It is nice when the results from a model are returned to me very quickly and I do not have to wait to queue on the university's super computers. I'm not very good at organization and planning so there's often spurts of heavy machine learning that have to be done and having all these compute resources at my disposal makes this possible. 

However, this isn't really what I should be concentrating on, should it? Instead of increasing my computational throughput, I should concentrate on being more organized. I think this is better for me as a researcher and as an individual. Here are some common places where my lack of organization causes me to do much more work:

- Often, I get results from something and then loose track of the file that I saved my results in. 
- I will generate features from some dataset using a particular feature extraction method, save the results to a matrix market file and then accidentally overwrite them a day later so that I have to rerun feature extraction.
- Frequently, I forget what features are contained in the particular matrix market files I've generated. To make sure that my evaluation results are not operating on erroneous data, I rerun feature extraction. 
- I forget exactly which parameters I used for hyperparameter searching. Broader hyperparameters may achieve better results and it's always a good idea to make sure that you're not comparing models at different levels of optimization. This in mind, I'll often have to rerun machine learning experiments with the expanded set of hyperparameters

I write these because I think it's good for me to point them out to myself. I also think it might be helpful for anyone who stumbles across this to wonder if they have additional work because of disorganization in their research procedure too. 

# Why Pachyderm?
This tool seems like an excellent way to organize myself. I'm not particularly concerned with the productionalized aspects (like the ability to rerun machine learning pipelines as new data comes in).    

I'm more interested in the ability to store files in repos and have separate output repos for each experiment. 

I want to be able to separate my code for one experiment into its own repo and then to direct the output of each of those repos into their own separate output repos (keeping the input and output separate for a single experiment isn't super important for my task but it sounds like something pachyderm does automatically judging by the sample code on [the beginner tutorial](http://pachyderm.readthedocs.io/en/latest/getting_started/beginner_tutorial.html) seems to indicate.)

In addition, I am comfortable with vms and okay with lxc/lxd containers. However, kubernetes and docker are not something I'm comfortable with. 

I have docker installed but I'm usually just running commands someone else told me to run. I don't understand the container infrastructure underlying docker and k8. lxc and lxd containers so closely mirror vms, the learning curve there was not very steep. Docker seems to have a whole series of other jargon and tools. 

## First steps

I created a rancher vm template on proxmox with my public keys in the appropriate cloud-config.yml file using the instructions described [here](http://rancher.com/docs/os/v1.2/en/running-rancheros/server/install-to-disk/). This way, I don't have to use ansible to move all the keys over after cloning them.

I set up 6 vms from this template. Each have 4 gb of ram, 4 processing cores and 100 GB of disk. I'm starting small because I'm not sure how well this will work out (also most of my ram is tied up in my dl580 which needs 70 GB to boot).

I started kubernetes in rancher and after all the hosts were added and all the services started, I began looking into how to set up pachyderm. 

## Bucket storage
I set up an lxc container in proxmox to hold my minio s3 compatible storage at the recommendation of the pachyderm intro site. This appears to be functioning correctly, I can upload to buckets and even access via mc. 

### Rookie mistake? 
I didn't realize that minio could be set up ontop of kubernetes for a distributed object store. I wonder if this was the better option to take (the lxc containers resources could then be torn down for another rancher clone).

## Persistent volume storage
The pachctl deploy command `pachctl deploy custom --persistent-disk google --object-store s3 <persistent disk name> <persistent disk size> <object store bucket> <object store id> <object store secret> <object store endpoint> --static-etcd-volume=${STORAGE_NAME} --dry-run > deployment.json` listed on the [on premises deploy documents](http://pachyderm.readthedocs.io/en/latest/deployment/on_premises.html), refers to a persistent disk in google's cloud. I'd really rather use my own machines (since I have enough of them). So I'll have to look into that. 

The options for this parameter are google, aws and azure. However, all of these are cloud providers. I wonder if there's an open source clone that implements one of these apis. [This page](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) lists some types of persistent volumes but I'm unsure if these are compatible with pachy. 

Guess this is a good place to pick up next time I work on this. 
