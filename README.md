# YOLOv3-tiny-custom-object-detection
As I continued exploring YOLO object detection, I found that for starters to train their own custom object detection project, it is ideal to use a YOLOv3-tiny architecture since the network is relative slow and suitable for small/middle size datasets


# Environment:
Ubuntu 16.04
CUDA 9.0
GPU: Geforce GTX 1080

# Great sources:

https://github.com/AlexeyAB/darknet 

https://github.com/AlexeyAB/Yolo_mark 

# Step 1:
 Go to YOLO website https://pjreddie.com/darknet/yolo/, follow the instructions and have your Darknet installed. 
 
# Step 2:
Compiling with CUDA and OpenCV, here is the instruction: https://pjreddie.com/darknet/install/#cuda 
Make sure your can run before training your own dataset 

./darknet detector demo cfg/coco.data cfg/yolov3.cfg yolov3.weights

./darknet detector demo cfg/coco.data cfg/yolov3.cfg yolov3.weights <video file>
        
# Step 3:
Prepare your own labled dataset: 
Here is a great tool I used to annotate my own datasets: https://github.com/AlexeyAB/Yolo_mark
Remember, dataset is very crucial for deep learning and your model's performance, it is time consuming to prepare your own annotated dataset. 

# Step 4:
Copy all your prepared images and their corresponding .txt files to the directroy in your Darknet file:

./home/Darknet/data/img

# Step 5:
In Step 3, you should have created a txt file called : obj.names. 
Since I trained on 6 objects, I named my file as obj6.names and they are: babybuggy, bicycle, fire_engine, motor_cycle, scooter, moter_scooter. 
I have uploaded a sample obj.names file in this post. 



