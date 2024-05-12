**Driver Drowsiness Detection using Convolutional Neural Networks**

**Introduction**
1. Driver sleepiness is the primary factor that led to traffic accidents. To minimize collisions on the side of the road, it is essential and challenging to identify driver drowsiness (DDD) or fatigue.
2. To increase safety and stop these events, we'll develop a drowsiness detection system. When the system notices the driver is drowsy, it will alert (alarm) the driver.
3. We'll take pictures with a webcam to utilize as input. We'll make use of OpenCV's cv2 technique.
4. Since the OpenCV object detection method only accepts grayscale images as input, the image must be transformed to grayscale in order to identify the face in it.
5. It generates a list of detections with the height, the width of the object’s border-box, along with x, y, and coordinates. Now that the faces have been iterated, we may create boundary boxes for each of them.
6. The model can then be applied to the image to get a prediction. If the prediction is closer to 0, we display "Open" on the screen. In the absence of this, we display "Closed" (i.e., it's nearer 1).
   
   ![image](https://github.com/vamshiachavelli/Driver-Drowsiness-Detection-CNN/assets/58171768/a9e6e822-9946-494e-98a1-225cd79284c6)

   ![image](https://github.com/vamshiachavelli/Driver-Drowsiness-Detection-CNN/assets/58171768/0d57e085-aa8b-4cd9-ba79-2328c8ca6ce6)

**Dataset Description**
1. UMass Amherst open eye face data: More than 13,000 photos of faces were gathered from the internet for the data collection. The name of the individual pictured has been written on each face. 

2. Nanjing University closed eye face: This dataset includes 2423 subjects, including 1192 subjects with both eyes closed which were obtained directly from the Internet and 1231 subjects with both eyes open which were chosen from the Labeled Face in the Wild (LFW [2]) database.

**Algorithm**
1. The model we used is built using Convolutional Neural Networks (CNN).
2. A type of deep neural network called a convolutional neural network does exceptionally well at classifying images.
3. There are three layers that make up a CNN: an input layer, an output layer, and a hidden layer with many layers.

**Data Preparation**
Data pre-preprocessing:
The following dependencies are required to pre-process the datasets.
1. CMAKE: needed for the face recognition
2. DLIB: needed for the face
3. FACE_RECOGNITION: necessary for identifying the coordinates of the eyes in a face.
                           ![image](https://github.com/vamshiachavelli/Driver-Drowsiness-Detection-CNN/assets/58171768/d43b0b0b-8ff3-4510-b6d3-98e85f189552)

4. Calling the appropriate functions: We need two different functions to pre-process the data because we are using two distinct datasets. The only difference between the internal code and the external code is how we loop through the files in their respective folders.
                           ![image](https://github.com/vamshiachavelli/Driver-Drowsiness-Detection-CNN/assets/58171768/7152a981-5e39-4d9b-86d1-4131aa0e2dc1)
5. The coordinates are obtained by utilizing this snippet after each image has been fetched from its folder.
                           ![image](https://github.com/vamshiachavelli/Driver-Drowsiness-Detection-CNN/assets/58171768/0175851c-2d9c-4072-9e5a-6090175b6439)
6. Let's make a list to record the values of the coordinates after we have identified them for each eye. Pre-processing is skipped if the library is unable to identify the face.
7. Let's define the boundaries for each eye so that we can remove it from the face. We are extending the range by a cushion to ensure that the entire eye is photographed.
8. Adding a buffer zone around the coordinates
9. Now, we remove the eye from the face using the PIL image library's crop feature
                           ![image](https://github.com/vamshiachavelli/Driver-Drowsiness-Detection-CNN/assets/58171768/c4a1cc3c-f42b-40f2-8af8-eef380306dca)
11. Let's adjust the image now so that it has a standard size across the board for all images sent to the neural network.
12. In order to send it to training, we now create a folder, put it in that folder, and save it.
13. Above all steps are same for the closed_eye_data.
                          ![image](https://github.com/vamshiachavelli/Driver-Drowsiness-Detection-CNN/assets/58171768/fd7c2c93-7462-45a4-bed0-1fae3a3ff179)
                          ![image](https://github.com/vamshiachavelli/Driver-Drowsiness-Detection-CNN/assets/58171768/ded35dbf-b9e2-42b8-b0ee-7656348abd58)

**References**

Qaisar Abbas, “Hybrid Fatigue: A Real-time Driver Drowsiness Detection using Hybrid Features and Transfer Learning” International Journal of Advanced Computer Science and Applications (IJACSA), 11(1), 2020. http://dx.doi.org/10.14569/IJACSA.2020.0110173.

Sahayadhas, A.; Sundaraj, K.; Murugappan, M. Detecting Driver Drowsiness Based on Sensors: A Review. Sensors 2012, 12, 16937-16953.

Rateb Jabbar; Mohammed Shinoy; Mohamed Kharbeche; Moez Krichen; Kamel Barkaou : Driver Drowsiness Detection Model Using Convolutional Neural Networks Techniques for Android Application https://ieeexplore.ieee.org/document/9089484









