# Style_Transfer_and_object_segmentation

In this project, we seek to create a neural network that can apply style transfer only to a segmented portion of the image, for example: the foreground or the background. We intended to do this by combining two processes– image segmentation and style transfer.

We firstly aim to perform k-means clustering for image segmentation to preprocess and better understand our images. Following this step, we aim to utilize semantic segmentation techniques (specifically: the grab cut algorithm [1]) to select images (example: portraits) to separate the foreground from the background. We lastly intend to build a deep convolutional neural network that is capable of style transfer. After these three steps are performed individually, we apply the grab cut algorithm to a style transfer target image to produce an image with isolated style transfer; i.e. style transfer is applied only to the foreground or background.

Through the course of this project we also aim to perform an exploratory analysis on style transfer networks. Each member of the team will build their own style transfer network optimized for best performance. A comparative study will then be conducted on both these models to draw conclusions as to what it takes to build a stable, reliable and well performing convolutional deep network. Furthermore, an analysis is also conducted on VGG-19 (the style transfer network used) to better understand its internal workings using feature maps and saliency maps. 

![image](https://user-images.githubusercontent.com/55135185/159245905-0900b4a0-32a9-4ed8-bcac-f2fa8aa20eea.png)

# Methods

1. Image Segmentation using KMeans Clustering:

A preprocessing step is first conducted whereby image segmentation is performed using k-means clustering. The algorithm segments an image into discrete regions to gain a better understand of the components that exist within an image. This step was helpful in choosing the best images for the project. This analysis is also commonly used in other machine and deep learning tasks such as object segmentation, object recognition, content-based image retrieval etc. 

2. GrabCut Algorithm:

For the first processing step to meet our project goals, we used the GrabCut algorithm. This is an image segmentation algorithm that is based on graph cut optimization, gaussian mixture models, and Markov networks and is used to separate the foreground object within an image from the background. This is done by creating a user defined bounding box and grouping pixels into either foreground (source nodes) or background (sink nodes).

3. Style Transfer Network

For the second processing step to meet our project goals, each group member built a style transfer network. Both pytorch and tensorflow were used and each group member optimized their network to achieve best results. A style transfer network is created using a trained convolutional neural network (for the project, both team members used VGG-19) that takes in two input images (a style and a content image) and uses separate loss functions to create a single target image that combines the two features. 

4. VGG-19 Analysis

After the style transfer models were built, an analysis was done on the VGG-19 network to gain a better understanding as to how deep neural networks work and analyze information. This step was motivated by class discussions on ethical AI as well as Geirhos, Jacobsen, Michaelis et al (2020) [6] that states a large group of problems in deep learning today can be tied to the same issue:  Deep networks are not learning the way we think they are learning but using unintended learning strategies or shortcuts. This phase of the project aims to better understand how deep networks are learning by printing out feature and saliency maps. 

5. Comparative Analysis on Style Transfer Network

After both the style transfer networks were created, a comparative analysis between the networks was performed. This analysis was done to give insights into what it takes to build a stable and reliable network and to help us choose the best network for the final step of the project; the semantic segmentation style transfer implementation.

6. Semantic Segmentation Style Transfer Network (Style Transfer + GrabCut)

The last step of our project combines the best style transfer network with the grabcut algorithm to create a new type of tool. This network first performs style transfer to an image, and, using the target image obtained, grabcut image segmentation is performed to create an image where style transfer is only applied to the foreground or the background. 

# Results:

KMeans Clustering:

![image](https://user-images.githubusercontent.com/55135185/159247101-97d7559f-2fb3-41f7-b60c-7dd30b16c0f9.png)

The above figure depicts the discrete regions that lie within the image, each of these regions (black and grey) correspond to one of the two clusters that have been used. 

![image](https://user-images.githubusercontent.com/55135185/159247211-d577b779-8288-417c-8a06-45b735733a25.png)

To understand the importance of each cluster in the image, one of the two clusters has been blacked out. In the above image, cluster 1 (K=1) has been blacked out. The background and face correspond to cluster 1.

GrabCut Algorithm

![image](https://user-images.githubusercontent.com/55135185/159248280-5cef9e19-93a9-4815-ad9e-c45727d60eae.png)

Style Transfer:

![image](https://user-images.githubusercontent.com/55135185/159248529-988903cc-fa41-497a-b3d9-5f7e9f54b13a.png)

![image](https://user-images.githubusercontent.com/55135185/159248620-76b02817-4ef2-42db-b3fc-66e043c9fed9.png)

# Comparitive Study

![image](https://user-images.githubusercontent.com/55135185/159248732-5f56a8dc-a6aa-4524-87c1-ffdb82723c49.png)

The above two images correspond to the target images generated by the two style transfer networks. The image on the left was generated by the network developed using Pytorch. The image on the right was generated by the network developed using Tensorflow. 

With better computational power and extensive hyper=parameter tuning tensorfow can generate promising results

![image](https://user-images.githubusercontent.com/55135185/159249158-5cd2d47e-cb76-42b7-9d76-b50585b21bfe.png)

Segmentation Style Transfer:

![image](https://user-images.githubusercontent.com/55135185/159249241-e273f8ea-5f57-40f1-9304-296891d1c6c3.png)





