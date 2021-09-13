# Gestures recognition for computer navigation
This is a Jupyter notebook for gesture recognition and gesture recognition events such as using a mouse or changing the volume.

The video recognition is performed by [OpenCV](https://opencv.org/) and the hand landmark tracking is done through [MediaPipe](https://google.github.io/mediapipe/solutions/hands.html). The gesture recognition is handled through a simple one hidden layer neural network set up with [Pytorch Lightning](https://www.pytorchlightning.ai/). 


### Data gathering and training process
To collect coordinates for training the model, I recorded MediaPipe-tracked hand gestures for 20 seconds at a time. For each gesture, one recording was taken for the left hand, and an additional one for the right hand. The x coordinates for the right hand were then flipped. This resulted on average in about ~1000 sets of coodinates collected for each set of gestures. These are in the training_data.csv folder. All coordinates were normalized to the wrist handmark's coordinates. 80% of the data was used for training, and 20% for validation. Although it had to be trained for twice as many epochs, I found that a one hidden layer neural network with 256 neurons had the same validation loss (~0.04) as one with an extra hidden layer, so ultimately that's the neural network used in this notebook.


### The currently recognized hand gestures:

https://user-images.githubusercontent.com/68296887/133141548-0266426f-5d77-4d56-a495-178969c3d2dc.mp4

### Gesture events that are currently in the notebook:

* Using a mouse, scrolling, and zooming:

https://user-images.githubusercontent.com/68296887/133141571-9be1a8dd-adea-4a77-992c-3afe618409e6.mp4


* Pausing a video and changing the volume:

https://user-images.githubusercontent.com/68296887/133141588-7a9f8915-7b10-4022-9a77-61a877e0ca86.mp4


* Browser navigation:

https://user-images.githubusercontent.com/68296887/133141580-77298275-852d-4c74-9b3a-98468a1f299b.mp4


## Usage

If you would like to use the notebook with my pretrained weights, please download 100epochs.pth and run all the cells in part 1 (initializations) and part 3 of the notebook. If you would like to train the model on your own gestures, please follow part 1 and part 2 of the notebook. 
