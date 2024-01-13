# Face-recognition-and-identification

This is a practice project of mine to get working understanding of CNNs and it's capabilities in face identification by using transfer learning.

Model used here is VGG-Face model which is created with the [weights](http://www.robots.ox.ac.uk/~vgg/software/vgg_face/ "VGG Face Descriptor") contributed by the authors of the paper [Deep Face Recognition](http://www.robots.ox.ac.uk/~vgg/publications/2015/Parkhi15/parkhi15.pdf "Paper") 

## Files
### avg_face_enc_gen.py
This program promts for a name to save the encodings and takes in the camera feed and identifies the face using [Haar Cascade Classifiers](https://docs.opencv.org/3.3.0/d7/d8b/tutorial_py_face_detection.html "Face detection using Haar cascades") and VGG-Face model is loaded and the program captures 40 pictures of your face and each face is separately encoded with the model and averaged with all fourty encodings of the face.

### face_recognition.py
This simply works like a camera with feature of identifying the people in the camera if they have already saved their encodings using the previous program.

#### Note
Make sure you download the haarcascade_frontalface_alt.xml file along with the model from the this [link](https://drive.google.com/drive/folders/1BlXwPb3b6gai_OtYMnvFMWobzfY4Xba6?usp=sharing)


Setup requirements:
Webcam , SD card, led indicator, Trigger Button
Required Phases:
Phase 1:
1)Online Face Training:
1. Image acquisition: Image is acquired using a high definition camera which is placed in
the classroom. This image is given as an input to the system.
2. Dataset Creation: Dataset of students is created before the recognition process.
Dataset was created only to train this system. We have created a dataset of 60 students which
involves their name, roll number, department and images of student in different poses and
variations. For better accuracy minimum 40 images of each students should be captured
3 .Storing: We have used Numpy Array to store the student’s data in npy file

2)Offline Attendance:
The Interface includes a camera with an SD card which is used to capture the student
images locally and transfer these images to the server for comparison and attendance
generation once the internet is available.

3)Online Reporting in Excel:
When there is a reliable internet connection the data is forwarded to the cloud server
which then runs the proprietary face recognition algorithm and generates the attendance in a
excel format

Phase 2:
1)Freeze Camera:
Once the student is in front of the camera for giving attendance, the camera must capture 150
frames in 3 seconds and give a indication that the attendance has been recorded
(Requirements 3 Seconds, 90% Accuracy)

Phase 3:
1)Database Integration:
The proprietary Face recognition application and the encodings of the trained students are
stored in the postgres database.
2)Stand Alone application:
Our algorithm is running in the postgres database which compares the images taken through
camera and stored in the sd card with the encodings of the trained images and then generates
the attendance in a excel format.

Constraints faced :
1)Freeze camera :
The whole concept of storing the image in the sd card and then comparing in the later stage
may lead to decrease in accuracy as the model is built for live capturing.
Proposed model:
Our algorithm works based on live image capturing and then compares the captured
encodings with the encodings captured during the training phase and updates the excel sheet
on the go.The whole model is proposed with Python,openCv,Numpy.