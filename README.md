# Live car object detection using YOLOV10
#### Video Demo:  <https://youtu.be/rlNcfBMK1lc>
#### Description:
This project is an object detection program oriented mainly for cars, which uses the YOLOV10 from Ultralitycs. The later is one of the so-called state-of-the-art real-time object detection and segmentation models. At least it is one of the top 3 at the current time, based on speed and accuracy for computer vision object detection models. 

This program has three main steps: obtaining path to video file, detecting and labelling cars in real time, and saving the results as an output MP4 file. The first one is accomplished by the `arguments()` function. `arguments()` gets the path to the video file in which the real-time detections are going to be made. For this, the user must provide a commnad-line-argument for the name of the video file. To get the file path, use of the `argparse` library was made.

In the second step, `get_car_detections()` first obtains all of the frames and information of the video with the `supervision` library. This allows the program to change and optimize parameters such as text size and font, bounding box thickness and labels.  Then, a quick implementation of the YOLO model is made with use of the `supervision`and `ultralytics` libraries. Since the YOLO models are trained mainly for detecting several types of objects some documentation on filtering object detections was required. After some reading and testing, the detections were filtered out, not only as a list of the results, but in the annotations as well. 
These are, filtetered exclusively by `class id` to get only car detections. After those detections are recorded, then the corresponding labels and boxes are annotated and, finally, every copy of the edited frame with the results is saved and shown live with use of the `cv2` library.

The last step is performed by `output_detection()`, which takes as input the list of the edited frames, and the height and width of the frames. Finally, with the `cv2` library every frame is used in a loop to create the video with the arguments previously mentioned and a default fps of 30, which can be changed using this open-source code of the program. 

### Is this project in the final phase?
Short answer: no. Actually, the first attempt to come out with this project was directed towards identifying license plate numbers implementing an OCR component to the program and a YOLOV10 model trained with a custom dataset already labelled with more than 10 k license plate images. However, I did not notice that the even the lightest and more optimized version of the YOLOV10 model, which is the YOLOV10N, needed so many resources to be trained. And yes, this is not a confusion, I purposedly try to implement the license plate recognition program with the V10 model since the dataset was only available for this version of YOLO. 

I did my research on the parameters that are of most relevance and found out that training should be carried with 300 epochs at least, just to obtain robust results. However, my current computational resources only allowed me to train this model for 1 day which basically allowed me to train the model for 1 epoch. Of course, the detections were not anywhere near of a decent project to show. This was the call for me to maybe try a base implementation of that idea, which was the reason this project is published only as a live car object detection. 

It is also important to notice that the program can also perform the live detection of different objects, not only cars as shown in this project.

In the near future, my objective is to get hands-on some more resources in order to train the license-plate model and implement the license plate OCR program. Basically with the main objective of implementing it here where I live, in Colombia, for parking lot systems. 
