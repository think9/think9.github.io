---
layout: post
title: Road Lane Detection
subtitle: Find lane on road using openCV
---

# Road Lane Detection using openCV

![result](https://user-images.githubusercontent.com/50393277/67205550-eea41a00-f44a-11e9-981a-043df2dd0190.png)

[Source Code](https://github.com/think9/Road-Lane-Detection)

## How to use

To run this program, you need those libraries.

* openCV
* numpy
* matplotlib

Open **Road_Lane_Detection.py** and replace it with your filename.

After run the program, you can see the first frame of your image.

Select ROI which contain road lane and press enter.

Program will find road lane in your video.

* To save image of each frame, just delete the annotation.

## Basic idea

Most lane detection program uses **cv2.inRange** function to find lane. It has a great performance but not good for any other videos. Because, in some videos, if pixel values are low then program cannot find any areas.

In this program, we select the ROI before running program. So we can find color area of lane in ROI and trace it.

## Process

![flow](https://user-images.githubusercontent.com/50393277/67205546-ee0b8380-f44a-11e9-9f4a-fc62e569c04e.jpg)

* Select ROI

After run the program, select ROI in first frame of video.

* Gaussian Smoothing

First we need to smooth the image. It is helpful to reduce image noise so we can get better result.

* Histogram

Histogram is counting set of each pixel values. In ROI, the brightest area is lane because it has a white color.

![hist](https://user-images.githubusercontent.com/50393277/67205548-eea41a00-f44a-11e9-91ea-a9783a58799b.png)

In above hisgorams, we find local maximum value from right side. It is bright area so around of maximum value of index is the lane's pixel value.

* Edge Detection

![canny](https://user-images.githubusercontent.com/50393277/67205552-ef3cb080-f44a-11e9-8fb4-9498aa5814e5.png)


Apply Canny Edge detecion to find edges in frame.

* Hough Transform

After we find white areas we detect lines in frame. That is the lane on the road!

![result](https://user-images.githubusercontent.com/50393277/67205550-eea41a00-f44a-11e9-981a-043df2dd0190.png)

## Issues

Most of issues are occured when we find white areas in frame. Because we find all of white areas on frame.

For example, white road signs on road are recognized as lane because it has white color similar with lane.

![issue](https://user-images.githubusercontent.com/50393277/67205549-eea41a00-f44a-11e9-960d-bf0643aed27e.png)

For solve this problem, we need to segement objects.
