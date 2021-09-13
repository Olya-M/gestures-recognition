# Gestures recognition for computer navigation
This is a Jupyter notebook for gesture recognition and gesture recognition events such as using a mouse or changing the volume.

The video recognition is performed by [OpenCV](https://opencv.org/) and the hand landmark tracking is done through [MediaPipe](https://google.github.io/mediapipe/solutions/hands.html). The gesture recognition is handled through a simple one hidden layer neural network set up with [Pytorch Lightning](https://www.pytorchlightning.ai/). 
To collect coordinates for training the model, I recorded MediaPipe-tracked hand gestures for 20 seconds at a time. For each gesture, one recording was taken for the left hand, and an additional one for the right hand. The x coordinates for the right hand were then flipped. This resulted on average in about ~1000 sets of coodinates collected for each set of gestures. These are in the training_data.csv folder. All coordinates were normalized to the wrist handmark's coordinates. 

If you would like to use the notebook with my pretrained weights, please download 100epochs.pth and run all the cells in part 1 (initializations) and part 3 of the notebook. If you would like to train the model on your own gestures, please follow part 1 and part 2 of the notebook. 

The currently recognized hand gestures:
![The recognized hand gestures](https://imgur.com/t2ghivn.gif)

Using a mouse, scrolling, and zooming:
![Recognized hand gestures used for controlling a mouse, scrolling, and zooming](https://imgur.com/INHsXwU.gif)

Pausing a video and changing the volume:
![Recognized hand gestures for pausing a video and the volume](https://imgur.com/XBvrZPt.gif)

Some window and browser navigation navigation:
![Recognized hand gestures for browser nagivation](https://thumbs.gfycat.com/SeveralSameAmazontreeboa-size_restricted.gif)
