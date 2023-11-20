How to reproduce training?
--------------------------

1. git clone https://github.com/kowndinya-renduchintala/EfficientGuys23.git
2. cd reproduce-train
3. docker build -f ./Dockerfile.train -t kowndinya_reproduce .
4. docker run --gpus "device=0" --rm -ti kowndinya_reproduce

Generated artifacts pushed to HuggingFace Hub: [kowndinya23/flan2022-512-mistral-graphcut-logdet-sub11-reproduce](https://huggingface.co/kowndinya23/flan2022-512-mistral-graphcut-logdet-sub11-reproduce/tree/main)

### Dataset used: 
[kowndinya23/flan2022-mistral-512-450K-graphcut-logdet](https://huggingface.co/datasets/kowndinya23/flan2022-mistral-512-450K-graphcut-logdet)

Subset of FLAN 2022. The total dataset size is ~17.5M instances. However, the dataset used is a subset of size 450K.

### TO DO
Add script for dataset curation

### How was the dataset created?
First, filter out instances based on len(prompt)+len(response)<=512.
Then use a data subset selection technique based on submodular functions -  graphcut and logdet.
This step is supposed to select samples that are representative and diverse instead of just selecting some random subset.
