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

`yolo detect train data=coco.yaml model=yolov10n/s/m/b/l/x.yaml epochs=500 batch=256 imgsz=640 device=0,1,2,3,4,5,6,7`
