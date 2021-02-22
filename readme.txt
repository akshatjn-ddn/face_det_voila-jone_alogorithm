We will be using Haar Cascade algorithm, also known as Voila-Jones algorithm to detect faces. It is basically a machine learning object detection algorithm which is used to identify objects in an image or video. In OpenCV, we have several trained  Haar Cascade models which are saved as XML files. Instead of creating and training the model from scratch, we use this file. We are going to use “haarcascade_frontalface_alt2.xml” file in this project. 

he read() function returns:

    The actual video frame read (one frame on each loop)
    A return code

The return code tells us if we have run out of frames, which will happen if we are reading from a file. This doesn’t matter when reading from the webcam since we can record forever, so we will ignore it.

For this specific classifier to work, we need to convert the frame into greyscale.
The faceCascade object has a method detectMultiScale(), which receives a frame(image) as an argument and runs the classifier cascade over the image. The term MultiScale indicates that the algorithm looks at subregions of the image in multiple scales, to detect faces of varying sizes.
et us go through these arguments of this function:

    scaleFactor – Parameter specifying how much the image size is reduced at each image scale. By rescaling the input image, you can resize a larger face to a smaller one, making it detectable by the algorithm. 1.05 is a good possible value for this, which means you use a small step for resizing, i.e. reduce the size by 5%, you increase the chance of a matching size with the model for detection is found.
    minNeighbors – Parameter specifying how many neighbours each candidate rectangle should have to retain it. This parameter will affect the quality of the detected faces. Higher value results in fewer detections but with higher quality. 3~6 is a good value for it.
    flags –Mode of operation
    minSize – Minimum possible object size. Objects smaller than that are ignored.

The variable faces now contain all the detections for the target image. Detections are saved as pixel coordinates. Each detection is defined by its top-left corner coordinates and width and height of the rectangle that encompasses the detected face.

rectangle() accepts the following arguments:

    The original image
    The coordinates of the top-left point of the detection
    The coordinates of the bottom-right point of the detection
    The colour of the rectangle (a tuple that defines the amount of red, green, and blue (0-255)).In our case, we set as green just keeping the green component as 255 and rest as zero.
    The thickness of the rectangle lines
