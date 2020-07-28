
# VAID_dataset

## Introduction

VAID(Vehicle Aerial Imaging from Drone) dataset contains 6000 aerial images under different illumination conditions, viewing angles from different places in Taiwan.The images are taken with the resolution of 1137 * 640 pixels in JPG format. Our VAID fataset contains seven classes of Vehicles, namely 'sedan' , 'minibus' , 'truck' , 'pickup truck' , 'bus' , 'cement truck' , ' trailer'.  
From left to right in the figure below are labels 'sedan' , 'minibus' , 'truck' , 'pickup truck' , 'bus' , 'cement truck' , ' trailer'
![image](https://github.com/KaiChun-RVL/VAID_dataset/blob/master/images/class.PNG)
You can download VAID dataset in the website.https://vision.ee.ccu.edu.tw/aerialimage/




## Test model

We test VAID dataset on 5 common model including Faster R-CNN, Yolov4, MobileNetv3 , RefineDet and U-Net.

### Perfromance

### How to use 
 
#### Faster R-CNN
environment : tensorflow1.4 cuda9.2
1. Download the file
2. Put for_download/faster rcnn/data and for_download/faster rcnn/output into VAID_dataset/tf-faster-rcnn
3. Download dataset and put the fold Annotations amd JPEGImages into VAID_dataset/tf-faster-rcnn/data/VOCdevkit2007/VOC2007
4. make at VAID_dataset/tf-faster-rcnn/lib and VAID_dataset/tf-faster-rcnn/data/coco/PythonAPI

command :<br>
demo<br>
GPU_ID=0<br>
CUDA_VISIBLE_DEVICES=${GPU_ID} ./tools/demo.py --net res101 --dataset pascal_voc<br>

train<br>
./experiments/scripts/train_faster_rcnn.sh 0 pascal_voc res101

test<br>
./experiments/scripts/test_faster_rcnn.sh 0 pascal_voc res101

#### Yolov4
environment : cuda10.0 , cudnn>7.0 , opencv>2.4
1. Download the file
2. Put the folders for_download/yolov4/3rdparty , for_download/yolov4/backup , for_download/yolov4/cfd , for_download/yolov4/data , for_download/yolov4/include and for_download/yolov4/src into VAID_dataset/Yolov4/darknet
3. make in VAID_dataset/Yolov4/darknet
4. ./darknet if you succeed to make ,you will see usage: ./darknet <function>
5. put for_download/yolov4/yolov4.conv.137 into VAID_dataset/Yolov4/darknet
6.Download dataset and put the fold Annotations amd JPEGImages into VAID_dataset-master/Yolov4/darknet/VOCdevkit VOC2007 and VAID_dataset-master/Yolov4/darknet/VOCdevkit VOC2007_test

command:<br>
train <br>
./darknet detector train cfg/voc.data cfg/yolo-obj.cfg yolov4.conv.137
calculate map <br>
./darknet detector map cfg/voc.data cfg/yolo-obj.cfg backup/yolo-obj_best.weights 
test <br>
./darknet detector test cfg/voc.data cfg/yolo-obj.cfg backup/yolo-obj_best.weights
If you want to know more command , you can see the official yolo github.
#### Mobilenetv3

#### RefineDet
environment : cuda9.2 , pytorch 1.4.0
1. modify home path in VAID_dataset-master/RefineDet.PyTorch-master/data/config.py
2. modify VOC_ROOT path in VAID_dataset-master/RefineDet.PyTorch-master/data/voc0712.py
3. Download dataset and put the fold Annotations amd JPEGImages into VAID_dataset-master/RefineDet.PyTorch-master/data/VAID
4. put for_download/Refinedet/weights into VAID_dataset-master/RefineDet.PyTorch-master

command:<br>
train <br>
./train_refinedet320.sh
calculate map <br>
./eval_refinedet.sh 








