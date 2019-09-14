# CBIR
## Content-Based Image Retrieval

### Feature Extraction

There are many different ways to extract features from images, and I tried several. 
  
My goal is to create the best-performing Content-Based Image Retrieval System. I wanted to achieve a baseline, so I began by using a color histogram for each image and then calculating the nearest neighbor based on chi-squared distance. This algorithm performed horribly scoring a 0/11 matches, but it did provide a nice framework for the other models to come. 

The KAZE algorithm returned 0/11 matches. Even when returning the top 3 matches, none of the results matched the label of the query image. The matches were consistently around 0.6, which is alright, but still not returning the correct match. 

Similarly, the ORB algorithm returned 0/11 matches. The matches were consistently around 0.3, which is pretty bad. 
 
Image-Hashing with **VP-Trees** worked, but did not return any matching images. This is designed to return images that are the same or nearly the same, but the only semi-matching result was querying 'Four Grain' and the result being 'Four Roses.'

The packages I used for the VP-Trees model include:

* numpy - to convert the assigned hash value to a float and then to an intccv

* cv2 - to read and show the images

* imutils - image processing and moving

* pickle - for saving data nearby

* vptree - vantage-point tree, the star algorithm that assigns images unique values based on their composition and calculates the distance between them. 

* time - keeping track of how long things take (not necessary) 

![Fully Subdivided Vantage Point Tree](https://i.imgur.com/141xhIo.png)
(Fully subdivided vantage point tree)

I have been able to extract the features from the image database using the KAZE algorithm. I will be testing this method with the 11 query images this week. 

### Next Steps

I tried a simple neural network through Keras. It required me to designate how many classes/brands were in the training data. I split the file names and found there were about 350 unique brands of liquor. Still, I received errors about the input shape and the array shape not matching. This is somehting I would like to solve. 

I attempted to setup a convolutional denoising autoencoder, but it is very time-consuming to run and difficult to debug. 
