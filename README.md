# Detecting vehicles and its no plate using yolov8 on custom dataset

Download the vehicle number plate data using Roboflow dataset. Enter your own api_key by fixing the export in YOLOv8 format.
```
!pip install roboflow

from roboflow import Roboflow
rf = Roboflow(api_key="--------------------")
project = rf.workspace("roboflow-universe-projects").project("license-plate-recognition-rxg4e")
dataset = project.version(4).download("yolov8")
```

Install the dependency
```
!pip install ultralytics
```

Train the model using YOLOv8 on custom dataset.
```
!yolo task=detect mode=train model=yolov8n.pt imgsz=640 data="/content/License-Plate-Recognition-4/data.yaml" epochs=10 batch=8 name=yolov8n_custom
```

In case you don't want to train the model like I did you can simply use weight best.py 
```
!yolo task=detect mode=val model='/content/runs/detect/yolov8n_custom7/weights/best.pt' name=yolov8n_eval data='/content/License-Plate-Recognition-4/data.yaml' imgsz=1280
```

Testing the number plate detection on a video sample.mp4. Save the output video as sample_out_mp4.mp4.
```
!yolo task=detect mode=predict model='/content/runs/detect/yolov8n_custom7/weights/best.pt' source=/content/sample.mp4 show=True imgsz=1280 name=yolov8n_v8_50e_infer1280 hide_labels=True
```

Now, using sample_out_mp4.mp4 video to get detections on the vehicles as well using the pretrained YOLOv8 model.
```
!yolo task=detect mode=predict model=yolov8n.pt source=/content/sample_out_mp4.mp4
```

Results on validation dataset
![val_batch2_labels](https://github.com/KansaraT/Detecting_vehicles_-_no_plate_using_yolov8_on__custom_dataset/assets/91043060/16274138-4671-42b5-aca3-1804ded7f6b7)


Results on a video

https://github.com/KansaraT/Detecting_vehicles_-_no_plate_using_yolov8_on__custom_dataset/assets/91043060/907a9bbf-2040-4e59-aaa3-ae8c58cc74d2



