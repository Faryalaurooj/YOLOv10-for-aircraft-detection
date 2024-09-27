# YOLOv10-for-aircraft-detection
we will use YOLOv10 for our custom dataset aircraft detection and classification

## Installation

Clone the repo

`git clone https://github.com/THU-MIG/yolov10.git`

`conda create -n yolov10 python=3.9`

`conda activate yolov10`

`pip install -r requirements.txt`

`pip install -e .`


## Training

For training from scratch, we need to place our dataset in the folder /home/faryal/Downloads/yolov10/yolov10/ultralytics/models/yolov10/datasets/aircraft_images and /aircraft_labels  and also copy obj.names in this folder. Then run the code split.py from this folder. It will create an output directory at location /home/faryal/Downloads/yolov10/yolov10/ultralytics/models/yolov10/output/images and /labels and each folder will contain test train val. We habe split our dataset in 60 ; 30 ; 10 percentage into train val and test folders:

'python split.py'


then from the directory /home/faryal/Downloads/yolov10/yolov10/ultralytics/models/yolov10/output run in terminal ; 


`yolo detect train data=aircraft.yaml model=yolov10n/s/m/b/l/x.yaml epochs=500 batch=256 imgsz=640 device=0,1,2,3,4,5,6,7`


`from ultralytics import YOLOv10`


`model = YOLOv10()`

 If you want to finetune the model with pretrained weights, you could load the pretrained weights like below

`model = YOLOv10.from_pretrained('jameslahm/yolov10{n/s/m/b/l/x}')`
or

`wget https://github.com/THU-MIG/yolov10/releases/download/v1.1/yolov10{n/s/m/b/l/x}.pt`

`model = YOLOv10('yolov10{n/s/m/b/l/x}.pt')`

`model.train(data='coco.yaml', epochs=500, batch=256, imgsz=640)`
