# Object Detection in an Urban Environment

## Project overview

Self-driving cars are one of the most interesting potential developments regarding transport and logistics.
Not only would they enable fleets of autonomous trucks to ship products, they might also lead to greater comfort and safety in personal transportation. Finally, having the possibilty to call cars on a whim, could change the culture of car ownership, reduce the number of cars dramatically and therefore also make cities less car and more human centric.

Object detection is probably the most important technology for self-driving cars. Knowing where to drive and especially, when to stop is crucial to not get anyone killed. This project is therefore exploring ways to augment pictures to improve the detection of cars, pedestrians and bikes in an urban environment.

## Set up

### Requirements
To run this code first install the libraries in the requirements.txt by executing

```
pip install -r requirements.txt
```

### Train model

Start with a pretrained model, which has to be downloaded at

```
http://download.tensorflow.org/models/object_detection/tf2/20200711/ssd_resnet50_v1_fpn_640x640_coco17_tpu-8.tar.gz
```

and moved to

```
/home/workspace/experiments/pretrained_model/
```

Execute the following code to extract it

```
cd /home/workspace/experiments/pretrained_model/

wget http://download.tensorflow.org/models/object_detection/tf2/20200711/ssd_resnet50_v1_fpn_640x640_coco17_tpu-8.tar.gz

tar -xvzf ssd_resnet50_v1_fpn_640x640_coco17_tpu-8.tar.gz

rm -rf ssd_resnet50_v1_fpn_640x640_coco17_tpu-8.tar.gz
```

To change the augmentation for the model training edit the pipeline_new.config file located in

```
experiments\reference\
```

by adding augmentation options. Possible options can be found in

```
https://github.com/tensorflow/models/blob/master/research/object_detection/protos/preprocessor.proto
```

To launch the training process execute

```
python experiments/model_main_tf2.py --model_dir=experiments/reference/ --pipeline_config_path=experiments/reference/pipeline_new.config
```

and to launch the evaluation execute

```
python experiments/model_main_tf2.py --model_dir=experiments/reference/ --pipeline_config_path=experiments/reference/pipeline_new.config --checkpoint_dir=experiments/reference/
```

### Monitoring

To monitor both the training and the evaluation, launch a tensorboard instance by running

```
python -m tensorboard.main --logdir experiments/reference/
```

### Notebooks

To experiment on the augmentation options, use

```
Explore augmentations.ipynb
```

```
Exploratory Data Analysis.ipynb
```
On the other hand, lets you get a glimpse on the data itself.

### Data
The data consists of a set of pictures located in the data folder and split into three sets:

-test (3 pictures)
-train (86 pictures)
-val (10 pictures)


## Dataset
### Dataset analysis
This section should contain a quantitative and qualitative description of the dataset. It should include images, charts and other visualizations.
### Cross validation
This section should detail the cross validation strategy and justify your approach.

## Training
### Reference experiment
This section should detail the results of the reference experiment. It should includes training metrics and a detailed explanation of the algorithm's performances.

### Improve on the reference
This section should highlight the different strategies you adopted to improve your model. It should contain relevant figures and details of your findings.
