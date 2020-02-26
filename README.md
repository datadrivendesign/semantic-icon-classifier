# Semantic Icon Classifier

## Requirements
Our code run on ``Python 2.7.12``.

You need to install the following Python packages. Please create a new environment using your own Python package management (e.g. ``virtualenv``, ``Anaconda``).
* keras 2.0.8
* tensorflow-gpu 1.3.0
* tqdm
* numpy

You can use our `requirements.txt` to setup your environment.

## Download data

`icon.zip`: [(Download)](https://drive.google.com/file/d/1D0CFmDP0xNSyfSkK7kUHnfP0HnpcKZc1)
Training is not requre for this file. You may need it testing, but not require. Warning: a ton of image files in one zip, becareful aftre you unzip it.

``data.zip``: [(Download)](https://drive.google.com/open?id=1SiD_U5ifjX1poJZzLB-MwvoUQBhutYzH)


What are inside this zip:
```
training_x.npy: training icons (require for both train and evaluation)

training_y.npy: training labels (require for both train and evaluation)

validation_x.npy: testing icons (require for both train and evaluation)

validation_y.npy: testing labels (require for both train and evaluation)

validation_metadata.json: meta information about each icon (require for both train and evaluation)

anomalies_embeddings.npy:

gmm_invalid_class.npy:

gmm_valid_class.npy:

x_train_class.npy:

y_train_embeddings.npy:

```

``saved_models.zip``: [(Download)](https://drive.google.com/open?id=16hUHUzxkGHHBRsgvfeLV_4gTD3-KFYIy)

What are inside this zip:
```
anomaly.pkl: trained Anomaly Detection model (require in model evaluation with anomaly detector)

inv_anomaly.pkl: trained Anomaly Detection model (require in model evaluation with anomaly detector)

datagen.pkl: file generated during training (require in model evaluation)
```

## How to train our icon classifier

#### Step 1

Unzip `data.zip` in current directory.

Create a folder call ``saved_models``. You don't have to worry about `datagen.pkl`, this file will be generated during the training process.

#### Step 2

```
python2 cnn_pretrain.py
```

At end of the training, you will see the following evaluation for both training and testing set printed:

```
Accuracy on train data is: 99.68
Macro precision
0.99665404376452
Macro recall
0.9966673171192078
...
Accuracy on test data is: 94.68
Macro precision
0.8748637458382006
Macro recall
0.8552836877294613
```
These results are evaluate without anomaly detector. Our trained model is ``small_cnn_weights_100_512.h5``[(Download)](https://drive.google.com/file/d/1Kq5agoiLSuv5_CVBlkf5F7iENtpyKyz8).


## How to evaluate your icon classifier from a trained model

#### Evaluate without anomaly detection
```

python2 cnn_pretrain.py --model_path ./saved_models/small_cnn_weights_100_512.h5
```

#### Evaluate with anomaly detection
```

python2 cnn_pretrain.py --anomaly --model_path ./saved_models/small_cnn_weights_100_512.h5
```

## Notes
* You can change any training hyperparameter in `settings.py`. Our default CNN training epoch is `100`.

## Contributions
* Paper: [Learning Design Semantics for Mobile Apps](http://interactionmining.org/rico)

## If you have any question or missing file, please contact:
* Jason Situ (junsitu2@illinois.edu)
