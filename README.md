# IBM-Capstone-Project
IBM Capstone Project 

This is my project for the **IBM Data Science Capstone project**. I decided work on an object detection problem on images in order to tell whether people are wearing masks or not. Object detection algorithms aim at answering two questions basically: Which objects are present on an image and what are the bounding box coordinates than contain those objects. Therefore, for training this object detection network, we need to provide the images and the annotation files containing the bounding box coordinates along with the class names of the objects contained within those images.


<p align="center">
<img src="https://github.com/amh28/IBM-Capstone-Project/blob/master/assets/ezgif.com-video-to-gif%20(2).gif" width="600" height="400" />
</p>


- I am using a deep learning network architecture called YOLO (short for You Only Look Once), using pretrained weights on the ImageNet dataset and then performing fine-tuning on my dataset. I introduce some modifications to a Tensorflow 2.0 YOLO v3 implementation found on the following repo: https://github.com/zzh8829/yolov3-tf2, for solving object detection on my custom problem. In order to use this repo, you should follow instalation instructions such as creating the virtual environments and installing dependencies.




# Training images
- I collected images from different datasets as well as my own images found on Google using web scraping. Those images are only used for educational purposes.

- Despite the fact that there exists Face mask datasets depicting only the faces of one person in an image, I couldn't find many annotated dataset sources of face mask images with subjects placed on different parts of the image. That is why I performed manual annotations of those images using the LabelImg tool (https://github.com/tzutalin/labelImg). Those annotations are found on this repo on the Annotations/ directory. You are free to use them and add more images for the benefit of others working on the same problem.

-There are currently 2749 images that were used for training. In order to develop a highly reliable face mask detector we would need far more training images for both classes.


# Trained Weights for Face Mask detection
-The weights file that I used for inference and for creating the demo video from above is on the checkpoints directory, and it's called: 

Finally, if you liked my work you can give it a Star ⭐! 😄





