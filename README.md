
# **Code Example** 
Code Example

For the sake of brevity, you should download docker and initialize a tensorflow environment. 
```
$ curl -sSL https://get.docker.com/ | sh

$ sudo docker run -it -p 8888:8888 tensorflow/tensorflow /bin/bash
```
You should restart your server if your sudo docker commands cannot execute.
You need to install git and nano. You can ignore this step if you already have it
```
$ sudo apt-get update

$ sudo apt-get install git nano

```
You can then clone this repository here 
```
$ cd home

$ git clone git://github.com/muhdamrullah/tensor-rohan

$ cd tensor-rohan

$ python loop_thru_eval.py ./evaluation_files/

```

... When you execute this command, you are evaluating the images in the evaluation folder and appending to a tf_submission.csv file. 
Make sure you clean the CSV file if you are starting fresh.

# **Retraining an Inception_v3 Model** 

To generate the tensorflow graphs in this Github, you need to retrain an Inception_v3 model trained on 1000 classes of ImageNet Large Visual Recognition Challenge from 2012. For more information on this approach, refer to the paper on http://arxiv.org/pdf/1310.1531v1.pdf. You may retrieve Tensorflow's publicly-available Inception v3 model at http://download.tensorflow.org/models/image/imagenet/inception-2015-12-05.tgz. 

To retrain, you can execute the command below

```
$ python retrain.py \
--bottleneck_dir=./tf_files/bottlenecks \
--how_many_training_steps 100000 \
--model_dir=./tf_files/inception \
--output_graph=./retrained_graph.pb \
--output_labels=./retrained_labels.txt \
--image_dir ./roof_dataset

```
...When you execute this command, you are re-training the Inception_v3 model at 100000 training steps and you are reading the folder called 'roof_dataset' that contains the labelled roof images sorted into four folders based on the labels. Please create these four folders at your own pace based on the labelled roof images given in Kaggle. 
