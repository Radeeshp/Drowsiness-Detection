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
#### Activity Diagram:
![1](https://user-images.githubusercontent.com/82216452/194000782-ab9595b6-7ef7-497d-a8d4-5bb40456487a.jpeg)

    
    

        
