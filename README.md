TFOD 2.0 Custom Object Detection Step by Step Tutorial

https://www.youtube.com/watch?v=XoMiveY_1Z4
https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/install.html

1. Clone the models from github
tfod 2.0 github
https://github.com/tensorflow/models

2. install Protobuf Installation/Compilation
https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/install.html

# From within TensorFlow/models/research/
protoc object_detection/protos/*.proto --python_out=.

3. COCO API Installation
!git clone https://github.com/cocodataset/cocoapi.git
cd cocoapi/PythonAPI
!make
cp -r pycocotools <PATH_TO_TF>/TensorFlow/models/research

4. Install the Object Detection API
# From within TensorFlow/models/research/
cp object_detection/packages/tf2/setup.py .
python -m pip install --use-feature=2020-resolver .

5. Test your Installation
# From within TensorFlow/models/research/
python object_detection/builders/model_builder_tf2_test.py

6  Create Training_demo folder
https://drive.google.com/drive/folders/1_ufGdFEimNk9XA8qRqs0Yz43adT8_Qsn


7.  Insatll labelimg
#Create a new environment
python -m venv tfod

#Activate it
source tfod/bin/activate  #Mac
.\tfod\Scripts\activate  #Win

# Update & install dependencies
python -m pip install --upgrade pip

pip install labelimg


8. Download tensor flow model zoo
https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf2_detection_zoo.md


9.  Create TensorFlow Records

# Create train data:
python generate_tfrecord.py -x [PATH_TO_IMAGES_FOLDER]/train -l [PATH_TO_ANNOTATIONS_FOLDER]/label_map.pbtxt -o [PATH_TO_ANNOTATIONS_FOLDER]/train.record

# Create test data:
python generate_tfrecord.py -x [PATH_TO_IMAGES_FOLDER]/test -l [PATH_TO_ANNOTATIONS_FOLDER]/label_map.pbtxt -o [PATH_TO_ANNOTATIONS_FOLDER]/test.record


10.  Change the path in pipeline.config
https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/training.html

11 train the model
!pip install opencv-python==4.5.5.64

!python model_main_tf2.py --model_dir=/content/training_demo/models/my_ssd_resnet101_v1_fpn --pipeline_config_path=/content/training_demo/models/my_ssd_resnet101_v1_fpn/pipeline.config


Export a Trained Model