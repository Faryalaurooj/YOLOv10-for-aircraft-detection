# YOLOv10-for-aircraft-detection
we will use YOLOv10 for our custom dataset aircraft detection and classification




![avainoairbase_2715_3649](https://github.com/user-attachments/assets/7d6cf820-edfd-4453-baed-394df5893ab6)

![HillAirForceBaseZOom19046mp_6753_5840](https://github.com/user-attachments/assets/f4314d8a-b852-478c-b6ca-7b2c00dead0c)



![myrhorodairbase_2930_7766](https://github.com/user-attachments/assets/60424fa7-b388-44d8-a808-6707964268e0)

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



![F1_curve](https://github.com/user-attachments/assets/3a92dcbe-b31f-48f8-8cd3-2d3a003500db)


![P_curve](https://github.com/user-attachments/assets/41d06b90-85f0-4332-b849-55e2f12b704e)

![PR_curve](https://github.com/user-attachments/assets/f139b4f1-cff7-4acb-b754-3d4ed04c9d

![R_curve](https://github.com/user-attachments/assets/1028ec8a-876c-4a45-9d32-686f3b996104)
f1)


## Validation
Copy best.pt file from /home/faryal/Downloads/yolov10/yolov10/runs/detect/train20/weights/ folder into the main folder /home/faryal/Downloads/yolov10/yolov10/ and then run the command 


`yolo val model=/home/faryal/Downloads/yolov10/yolov10/best.pt data=aircraft.yaml batch=16`



it will validate the results , check the results in validation results file. 

## Predict 
To run the prediction on test images run this command 


`yolo predict model=/home/faryal/Downloads/yolov10/yolov10/best.pt source=/home/faryal/Downloads/yolov10/yolov10/ultralytics/models/yolov10/output/test/images`

check the results in test_results file

