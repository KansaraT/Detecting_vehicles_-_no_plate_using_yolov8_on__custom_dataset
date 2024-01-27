# Detecting vehicles and its no plate using yolov8 on custom dataset


'
!pip install roboflow

from roboflow import Roboflow
rf = Roboflow(api_key="--------------------")
project = rf.workspace("roboflow-universe-projects").project("license-plate-recognition-rxg4e")
dataset = project.version(4).download("yolov8")
'
