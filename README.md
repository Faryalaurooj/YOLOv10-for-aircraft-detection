# YOLOv10-for-aircraft-detection
we will use YOLOv10 for our custom dataset aircraft detection and classification

## Installation

Clone the repo

`git clone https://github.com/THU-MIG/yolov10.git`

`conda create -n yolov10 python=3.9`

`conda activate yolov10`

`pip install -r requirements.txt`

`pip install -e .`

## Dataset 
For training from scratch, we need to place our dataset in the folder /home/faryal/Downloads/yolov10/yolov10/ultralytics/models/yolov10/datasets/aircraft_images and /aircraft_labels  and also copy obj.names in this folder. Then run the code split.py from this folder. It will create an output directory at location /home/faryal/Downloads/yolov10/yolov10/ultralytics/models/yolov10/output/train/images and /labels and similarly for val/images and /labels and similarly for test/images and /labels. We have split our dataset in 60 ; 30 ; 10 percentage into train val and test folders:


`python split.py`


## Training
Then from the directory /home/faryal/Downloads/yolov10/yolov10/ultralytics/models/yolov10/output run in terminal ; 


`yolo detect train data=aircraft.yaml model=yolov10s.yaml epochs=100  batch=32  imgsz=416 device=0`

It will start training the yolov10 model on your custom data


`from ultralytics import YOLOv10`


`model = YOLOv10()`

 If you want to finetune the model with pretrained weights, you could load the pretrained weights like below

`model = YOLOv10.from_pretrained('jameslahm/yolov10{n/s/m/b/l/x}')`
or

`wget https://github.com/THU-MIG/yolov10/releases/download/v1.1/yolov10{n/s/m/b/l/x}.pt`

`model = YOLOv10('yolov10{n/s/m/b/l/x}.pt')`

`model.train(data='coco.yaml', epochs=500, batch=256, imgsz=640)`


## Validation
Copy best.pt file from train/runs folder in the main folder and then run the command 


`yolo val model=/home/faryal/Downloads/yolov10/yolov10/best.pt data=aircraft.yaml batch=16`

it will validate the results , check the results in validation results file. 



