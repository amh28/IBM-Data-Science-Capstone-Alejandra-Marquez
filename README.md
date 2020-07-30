# IBM-Capstone-Project

IBM Capstone Project

This is my project for the **IBM Data Science Capstone project**. I decided work on an object detection problem in order to tell whether people are wearing masks or not. Object detection algorithms aim at answering two questions basically: Which objects are present on an image and what are the bounding box coordinates that contain those objects. I am using deep learning and I train an object detection network. I need to provide it with the images and annotation files containing the bounding box coordinates, along with the class names of the objects contained within those images.

All the steps towards the completion of this problem are documented on the following noteboooks:

1. Data Exploration Notebook.ipynb
2. Feature Preparation -Choosing train, val and test set.ipynb
3. Model*definition_and_training*.ipynb
4. Model Evaluation Notebook\_.ipynb

<p align="center">
<img src="https://github.com/amh28/IBM-Capstone-Project/blob/master/assets/ezgif.com-video-to-gif%20(2).gif" />
</p>

- I am using a deep learning network architecture called YOLO (short for You Only Look Once), using pretrained weights on the ImageNet dataset and then performing fine-tuning on my dataset. I introduce some modifications to the Tensorflow YOLO v3 implementation found on the following repo: https://github.com/zzh8829/yolov3-tf2, for solving object detection on my custom problem. In order to test mask - no mask detection you should clone that repo, follow installation instructions, such as creating the virtual environments and installing dependencies. After that you can replace the files contained on this repo.

After installing everything, in order to know how to use this repo, skip to the **How to use it** section.

# Datasets

Despite the fact that there exists Face mask datasets depicting only the faces of one person in an image, I couldn't find many annotated dataset sources of face mask images with subjects placed on different parts of an image. That is why I performed manual annotations of those images using the LabelImg tool (https://github.com/tzutalin/labelImg).

- The following datasets were used for our problem:
  . PASCAL VOC dataset (http://host.robots.ox.ac.uk/pascal/VOC/): I used a subset of these images and performed manual annotations.
  . Face Mask Detection dataset (https://www.kaggle.com/andrewmvd/face-mask-detection): A dataset containing both people with and without mask. This dataset comes with annotations.
  . RMFD dataset (https://github.com/X-zhangyang/Real-World-Masked-Face-Dataset): Face mask dataset with mostly high quality images. I performed manual annotations.
  . My own images found on Google collected using web scraping: I performed manual annotations and these images are for educational purposes.

* All annotations are found on the Annotations/ directory. You are free to use them and add more images for the benefit of others working on the same problem. All images are on the JPEGImages directory.

* There are currently 2749 images that were used for training. In order to develop a highly reliable face mask detector we would need far more training images for both classes.

# Loss function and network size

- I tweaked the model playing with loss function formulation and also compared detections obtained by the whole YOLO architecture and the Tiny version.

- It is also important to change bounding box number, otherwise we will obtain nan values when training.

- I also explain this on the Model*definition_and_training*.ipynb notebook.

# How to use it:

- After installing the original YOLO repo, you should add an replace all files found on this repo.

- The weights I obtained after training, which I also used for inference and for creating the demo video from above, is on the checkpoints/ directory called: yolov3_train_125.tf

- After adding and replacing those files, you can perform inference on an Image using the following command:

!python detect.py \
 --classes ./data/voc2012.names \
 --num_classes 3 \
 --weights ./checkpoints/**yolov3_train_125.tf** \
 --image ./data/**NAME_OF_YOUR_IMAGE** \
 **--yolo_max_boxes 300** \
 --yolo_iou_threshold 0.3\
 --yolo_score_threshold 0.3

- I also show how to perform inference from a jupyter notebook on Model*definition_and_training*.ipynb .
- In order to try it from a webcam or video, please refer to the commands specified on the Yolo repo.

# How to retrain it adding more images

- If you would like to retrain the network you would need to add new images and annotations to the JPEGImages and Annotations folders. Then create new train val test txt files with the new filenames and perform cross validation to create the best partition. You need to generate new training and validation TF.RECORDS for training a new network. Commands for generating them are found at the end of the Feature Preparation -Choosing train, val and test set.ipynb notebook.

- You can also change loss function to its original formulation in case it doesn't work for your problem.

Ps. If you liked my work, give it a Star! ⭐ 😄 🇵🇪
