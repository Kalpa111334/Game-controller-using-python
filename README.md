Game Controller using python and openCV 🕹❤👌

This project is a simple implementation of a game controller using Python and OpenCV. With this controller, you can control games using hand gestures captured by a webcam. This project is a great way to learn about computer vision, gesture recognition, and game development. let's start...............

To make this project you need to follow this step:-

Installation
Install package with pip

pip install cvzone==1.4.1
pip install mediapipe==0.8.3.1
Deployment
To deploy this project run

# Please Subscribe my youtube channel "Problem Solve with Ridoy"
import cv2
from cvzone.HandTrackingModule import HandDetector
from pynput.keyboard import Key, Controller

cap = cv2.VideoCapture(0)
cap.set(3, 320)
cap.set(4, 210)

detector = HandDetector(detectionCon= 0.7, maxHands= 1)
keyboard = Controller()

while True:
    _, img = cap.read()
    hands, img = detector.findHands(img)

    if hands:
        finger = detector.fingersUp(hands[0])
        if finger == [0,0,0,0,0]:
            keyboard.press(Key.left)
            keyboard.release(Key.right)

        elif finger == [1,1,1,1,1]:
            keyboard.press(Key.right)
            keyboard.release(Key.left)
         
    else:
        keyboard.release(Key.left)
        keyboard.release(Key.right)
        

    cv2.imshow("Problem Solve with Ridoy", img)
    if cv2.waitKey(1) == ord ("q"):
        break
