# CBIR
## Content-Based Image Retrieval

### Feature Extraction

There are many different ways to extract features from images, and I tried several. 
  
My goal is to create the best-performing Content-Based Image Retrieval System. I wanted to achieve a baseline, so I began by using a color histogram for each image and then calculating the nearest neighbor based on chi-squared distance. This algorithm performed horribly scoring a 0/11 matches, but it did provide a nice framework for the other models to come. 
 
Image-Hashing with **VP-Trees** worked, but did not return any matching images. This is designed to return images that are the same or nearly the same, but the only semi-matching result was querying 'Four Grain' and the result being 'Four Roses.'

The packages I used for the VP-Trees model include:

* numpy - to convert the assigned hash value to a float and then to an intccv

* cv2 - to read and show the images

* imutils - image processing and moving

* pickle - for saving data nearby

* vptree - vantage-point tree, the star algorithm that assigns images unique values based on their composition and calculates the distance between them. 

* time - keeping track of how long things take (not necessary) 

![Fully Subdivided Vantage Point Tree](https://i.imgur.com/141xhIo.png)

### Next Steps

Since SIFT and SURF are patented, I decided to check out ORB, the free alternative. ORB provides a list of keypoints and feature descriptors as vectors. Relating this information to a nearest neighbor, or bag of (visual) words is something I would like to explore further. 
 
I tried a simple neural network through Keras. It required me to designate how many classes/brands were in the training data. I split the file names and found there were about 350 unique brands of liquor. Still, I received errors about the input shape and the array shape not matching. This is somehting I would like to solve. 

KAZE was very slow to extract the features from the images. There should be a better implementation of this for a larger dataset. 

I attempted to setup a convolutional denoising autoencoder, but it is very time-consuming and difficult to debug. 
