# cs603ml-project
Distributed training using tensorflow using 2 servers

# Replicate training of model
## Get Dataset 

```sh
wget https://datashare.ed.ac.uk/download/DS_10283_3192.zip
unzip DS_10283_3192.zip -d largeToTrain
cd largeToTrain
tar -zxvf CINIC-10.tar.gz
rm -rf CINIC-10.tar.gz

```
## Create python environment
```sh
conda create -n ml403 python=3.8
conda activate ml403

pip install tensorflow

```

## In both server mention ip-addr:port and INDEX
```py
INDEX = 0
#---------------------------------------------DDS
import json
os.environ['TF_CONFIG'] = json.dumps({
  'cluster': {
    'worker': ['10.203.3.186:12345', '10.203.3.186:12346'],
  },
  'task': {
    'type': 'worker',
    'index': INDEX
  }
})
```

## Run Script
> at server1
```sh
python server1.py
```

> at server2
```sh
python server2.py
```


