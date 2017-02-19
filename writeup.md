#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

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

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps.

1. I converted the images to grayscale.
![alt text][image1]

2. I applied Gaussian Blur to make it more smoth and reduce the noise.
![alt text][image2]

3. Use Canny edge detection. I set the lower_bound to 50 and upper_bound to 150 in this project.
![alt text][image3]

4. I set a regutangular area to filter out any countent which is not in this area. I basically did it by the intuition of myself.
![alt text][image4]

5. This part is about transform to Hough Space and find the lines. One challenge is that you need to make the solid line segments into a straight line. The modification I made is that first you split all the line segments into the left part and the right part by their x cordinates. Then I sort the line segments by their y values in reverse order. And then you iterate those line segments and add the missing part. I did this process for both the left and right part separately.


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 



###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...