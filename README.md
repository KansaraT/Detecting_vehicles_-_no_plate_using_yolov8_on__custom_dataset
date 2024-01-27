# Detecting vehicles and its no plate using yolov8 on custom dataset

```
!pip install ultralytics
```

```
!yolo task=detect mode=train model=yolov8n.pt imgsz=640 data="/content/License-Plate-Recognition-4/data.yaml" epochs=10 batch=8 name=yolov8n_custom
```

```
!yolo task=detect mode=val model='/content/runs/detect/yolov8n_custom7/weights/best.pt' name=yolov8n_eval data='/content/License-Plate-Recognition-4/data.yaml' imgsz=1280
```

```
!yolo task=detect mode=predict model='/content/runs/detect/yolov8n_custom7/weights/best.pt' source=/content/sample.mp4 show=True imgsz=1280 name=yolov8n_v8_50e_infer1280 hide_labels=True
```

```
!yolo task=detect mode=predict model=yolov8n.pt source=/content/sample_out_mp4.mp4
```

