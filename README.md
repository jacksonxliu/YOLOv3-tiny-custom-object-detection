# YOLOv3-tiny-custom-object-detection
As I continued exploring YOLO object detection, I found that for starters to train their own custom object detection project, it is ideal to use a YOLOv3-tiny architecture since the network is relative shallow and suitable for small/middle size datasets


# Environment:
OS: Ubuntu 16.04\
CUDA 9.0\
cuDNN 7.0\
Tensorflow 1.8.0\
OpenCV 3.3.0

GPU:Nvidia Geforce GTX 1080


# Great sources:

https://github.com/AlexeyAB/darknet 

https://github.com/AlexeyAB/Yolo_mark 

# Step 1:
 Go to YOLO website https://pjreddie.com/darknet/yolo/, follow the instructions and have your Darknet installed. 
 
# Step 2:
Compiling with CUDA and OpenCV, here is the instruction: https://pjreddie.com/darknet/install/#cuda 
Make sure your can run those commands before training your own dataset 

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

# Step 6:
Create a "train.txt" file which including the directory and the names of your labeled images for training:

data/img/n02834778_12542.jpg\
data/img/n02834778_12545.jpg\
data/img/n02834778_12553.jpg\
data/img/n02834778_1255.jpg\
data/img/n02834778_12592.jpg\
data/img/n02834778_12604.jpg\
data/img/n02834778_12605.jpg\
data/img/n02834778_12643.jpg\
data/img/n02834778_12654.jpg\
data/img/n02834778_12655.jpg\
data/img/n02834778_12658.jpg\
data/img/n02834778_12673.jpg


# Step 7:

Create a "test.txt" file which including the directory and the names of your labeled images for testing, remember do not test on the same images which used for training already. 


data/img/n02834778_1313.jpg\
data/img/n02834778_1325.jpg\
data/img/n02834778_1339.jpg\
data/img/n02834778_1362.jpg\
data/img/n02834778_1365.jpg\
data/img/n02834778_1372.jpg\
data/img/n02834778_1380.jpg

# Step 8:
In Darknet file, there is a cfg file. Creat your own YOLOv3-tiny.cfg in that file. 
I have posted a sample "YOLOv3-tiny6.cfg" file which I used to train my model. 


# Step 9:
You can download a pretrained weight from: http://pjreddie.com/media/files/darknet53.conv.74 

# Step 10:
Now you can start your training by typing: ./darknet detector train data/obj6.data yolov3-tiny6.cfg darknet53.conv.74 \
The trained weights will be saved at your ../darknet/backup

# Step 10:
After you monitored the training for maybe 10,000 iterations, you can stop training and test out your model by typing:\
./darknet detector test data/obj6.data yolov3-tiny6.cfg backup/yolov3-tiny6_10000.weights data/test/babybuggy.jpg

