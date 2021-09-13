# Gestures recognition for computer navigation
This is a Jupyter notebook for gesture recognition and gesture recognition events such as using a mouse or changing the volume.

The video recognition is performed by [OpenCV](https://opencv.org/) and the hand landmark tracking is done through [MediaPipe](https://google.github.io/mediapipe/solutions/hands.html). The gesture recognition is handled through a simple one hidden layer neural network set up with [Pytorch Lightning](https://www.pytorchlightning.ai/). The device controls are handled through [AutoPy](https://github.com/autopilot-rs/autopy), [pynput](https://pynput.readthedocs.io/en/latest/), and [pycaw](https://github.com/AndreMiras/pycaw).

### The currently recognized hand gestures:

https://user-images.githubusercontent.com/68296887/133141548-0266426f-5d77-4d56-a495-178969c3d2dc.mp4

### Gesture events that are currently in the notebook:
In all the videos below, the "spock" gesture (the Vulcan salute) are set as an end gesture that closes the gesture recognition window. Most of the gesture recognitions are currently set up to only be triggered with the right hand for no particular reason.

#### Using a mouse, scrolling, and zooming:
https://user-images.githubusercontent.com/68296887/133141571-9be1a8dd-adea-4a77-992c-3afe618409e6.mp4

The mouse mode activates if you briefly hold up your right palm (opened or lightly closed). Bringing your index and middle fingers together triggers a mouse click. Scrolling mode turns on if you briefly hold your hand in a "shaka" gesture, and zoom mode if you briefly hold your hand in a "ily gesture" (shaka with an index finger up).

#### Pausing a video and changing the volume:
https://user-images.githubusercontent.com/68296887/133141588-7a9f8915-7b10-4022-9a77-61a877e0ca86.mp4

Here, the finger heart gesture presses the spacebar. Holding your right hand in an open or closed pinch, with the rest of the fingers forming a fist, triggers the volume changing mode. Changing the hand to a different gesture turns off the changing volume mode.


#### Browser navigation:
https://user-images.githubusercontent.com/68296887/133141580-77298275-852d-4c74-9b3a-98468a1f299b.mp4

Alt-tab triggers if you face a horizontally-angled palm towards yourself. Holding up different numbers of fingers opens up the first, second, third, or "last" tab in a browser. Pinch gestures (with the rest of the fingers still up) cycle through the tabs or close and open tabs. Although they are still usable, I've found the ring-finger and pinky-finger pinches to be a bit finicky for tracking. The left hand index and middle finger pinches are set to go forward or backward a page in a browser. Pinches with the thumb touching the middle finger joints are currently set to open up links or files. 

## Data gathering and training process
To collect coordinates for training the model, I recorded MediaPipe-tracked hand gestures for 20 seconds at a time. For each gesture, one recording was taken for the left hand, and an additional one for the right hand. The x coordinates for the right hand were then flipped. This resulted on average in about ~1000 sets of coodinates collected for each set of gestures. These are in the [training_data.csv](https://github.com/Olya-M/gestures-recognition/blob/main/training_data.csv). To see what gesture each label represents, please see the Jupyter notebook. All coordinates were normalized to the wrist handmark's coordinates. 80% of the data was used for training, and 20% for validation. Although it had to be trained for 100 vs 40 epochs, I found that a one hidden layer neural network with 256 neurons had the same validation loss (~0.04) as one with an extra hidden layer.

## Usage

If you would like to use the notebook with my pretrained weights, download [100epochs.pth](https://github.com/Olya-M/gestures-recognition/blob/main/100epochs.pth) and run all the cells in part 1 (imports) and part 3 of the notebook. Follow part 1 and part 2 of the notebook if you would like to train the model on your own gestures. 
