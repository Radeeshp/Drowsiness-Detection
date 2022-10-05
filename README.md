# Drowsiness-Detection

## Aim:
      This project was done to detect if the driver of the vehicle is drowsy and alert the driver using an alarm.

## Requirements:
      -Raspberry Pi
      
      -Packages required must be installed
      
      -Traffic Hat(optional)
      
      -python
      
      -usb camera
      
## Structure:
      -config.json
      -conf.py
      -detect_drowsiness.py
      -haarcascade_frontalface_default.xml
      -shape_predictor_68_face_landmarks.dat
## Working
      
  Using a camera we capture images of the  driver in real time and process these image , 
  
  we detect the eyes and mouth of the driver to determine if they are open or closed .
  
  If the eyes are closed for sometime or if the person yawns for sometime then the alarm is sound to wake up the driver.
  
### config.json :
        Its used  to get the configuration inputs from the user.
### conf.py :
        Its used to access the config.json file.
### haarcascade_frontalface_default.xml :
        Its a haarcascade based classifier used to detect human face.
### shape_predictor_68_face_landmarks.dat :
        Its used to extract data points for the eyes and mouth to calculate EAR and MAR.
### detect_drowsiness.py :
    
    -We get all the required imports(packages).And intialize all the counter variables.
    
    -Load the haar cascade for  face detection.
    
    -Create the facial landmarks predictor. 
    
    -Grab the indexes of the facial landmarks for left, right eye.
    
    -Start the camera stream.
    
    -We start looping over the frames from the video stream.
    
    -Clean these frames and convert it to grayscale.
    
    -Detect faces in the grayscale, and draw a bounding box surrounding the face.
    
    -Take the face thats closest to  the center as we dont need the passengers face.
    
    
    -Find the facial landmarks for the face region, then convert the facial landmarks (x,y) coordinate to a numpy array.
    
    -Using the numpy array calculate EAR and MAR by calling the respective functions.
    
    -Compare the EAR to the threshold value, and if greater then increment blinkcounter by 1.
    
    -If blink counter is greater than its threshold value then sound the alarm if not reset blink counter.
    
    -Using MAR we decide if the person is yawning.If the person is yawning and  if the number of times he yawns is  greater 
     than the threshhold sound the alarm otherwisne reset the yawn counter.
#### Activity Diagram :
![1](https://user-images.githubusercontent.com/82216452/194001340-f4a6476e-d56f-4b46-852d-9745570dcdfe.jpeg)

#### Functions Used :
     -def EAR(eye)
     -def MAR(mouth)
     -def euclidean_dist(ptA,ptB)
#### def EAR() :
     -We take 2 sets of points for vertical markers, and set of points for horizontal mmarker.
     -Calculate the euclidean distance between these points.
     -Then compute EAR using the obtained euclidean distances and the formula.
     -Return the EAR value.
##### Activity Diagram :
![Screenshot 2022-10-05 162138](https://user-images.githubusercontent.com/82216452/194043928-a5853713-f632-43f9-8075-2feb859a70a7.png)
#### def MAR():
      -Compute the euclidean distance between 3 sets of vertical mouth landmarks a,b,c.
      -Commpute the euclidean distance between 2 sets of horizontal mouth landmarks.
      -MAR=(a+b+c)/2*d
      Return the MAR value.
##### Activity Diagram:
 ![Screenshot 2022-10-05 162801](https://user-images.githubusercontent.com/82216452/194045127-2de80a87-7981-415f-91c5-9d6ccdf0d1af.png)
    

    
    

        
