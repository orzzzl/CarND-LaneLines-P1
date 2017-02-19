**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/1.jpg "1"
[image2]: ./examples/2.jpg "2"
[image3]: ./examples/3.jpg "3"
[image4]: ./examples/4.jpg "4"
[image5]: ./examples/5.jpg "5"
[image6]: ./examples/6.png "6"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps.

Firstly, I converted the images to grayscale.

![alt text][image1]

Secondly, I applied Gaussian Blur to make it more smoth and reduce the noise.

![alt text][image2]

Third, Use Canny edge detection. I set the lower_bound to 50 and upper_bound to 150 in this project.

![alt text][image3]

Fourth, I set a regutangular area to filter out any countent which is not in this area. I basically did it by the intuition of myself.

![alt text][image4]

Fifth, This part is about transform to Hough Space and find the lines. 
![alt text][image5]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by the following:

One challenge is that you need to make the solid line segments into a straight line. The modification I made is that first you split all the line segments into the left part and the right part by their x cordinates. Then I sort the line segments by their y values in reverse order. And then I iterate those line segments and add the missing part. I did this process for both the left and right part separately. It can be illustrate as following:
![alt text][image6]

As you can see the red part is what I add to make it a straight line.

###2. Identify potential shortcomings with your current pipeline


So of course there is lots of problems. The first biggest problem is that in step 3 I set up a poly region just by my intuition.
The goal is to filter out any other part which is outside the lane line. But what if the view point just changes a little and it won't fit into my region? And what if I change the resolution of my camera? This part should definitely be changed if we want to make our stuff practically useful.

Another potential issue is that we use Hough Space transformation and tunes a few parameters to find the lines. But I feel like this method is not robust enough. It's still not good enough to filtering any other lines out in our sight. I am wondering if their is any more advanced techniques other than tuning our hyper-parameters?


###3. Suggest possible improvements to your pipeline

I am fine with step 1- 3 after which I get a binary image after canny edge detection. Then after that I guess we should do some deep learning stuff to detech the lane lines.

I just have a feeling that it's not the right way to select a poly-region and tuning parameters to find it. Our method should be more general and robust that it should always do a good job whenever you put the camera, it's night or day, etc.

One thing I'm thinking about is that maybe after canny edge detection we can treat every pixel as a feature and build a neuron network out of it. And the pixel which is on the lane line will be marked as true while others will be marked as false. Then we can train it using some training data and let it figure it out itself.

And I am curious about if there is any other possibilities to improve it.
