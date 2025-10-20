# Convolutional autoencoder (CAE) Segmentation masks
This project addresses a variant of a convolutional autoencoder model that aims to predict segmentation masks, i.e., 
learning the characteristics of an object in an image and creating pixel-level predictions that accurately outline the shape  of the object. 
The training data was taken from https://www.kaggle.com/datasets/tapakah68/segmentation-full-body-tiktok-dancing dataset. 

From this dataset, one of the records containing 10 images and 10 annotations corresponding to the images was taken. 
The purpose of the model is to learn from 3 images the element to be segmented and make predictions on the rest of the images. 


## Segmentation masks
Segmentation masks are pixel-level annotations in an image that separate a specific object from the rest of the image. The mask provides precise pixel-level data, acting as binary (black and white) or categorical representations.


## Autoencoder
Autoencoders are a type of neural network that, due to their architecture, are forced to first learn to compress data into a form that extracts the characteristics important to the model, and then reconstruct it to best match the target data. 

Autoencoders are composed of three elements:
* The encoder, which captures important features by reducing size.
* Bottleneck (latent space), which connects the encoder and decoder, or in certain situations may have other functionalities.
* The decoder, which takes the compressed data and reconstructs it to best match the model's target.
  
In general, these types of networks are applied in models that aim to eliminate noise, detect errors, extract features, reconstruct images, etc.


## Model construction

As can be seen in the image below, the model uses the image through the input layer, learns to extract the relevant features (encoder), and then the decoder layers learn to construct the image with binary values (mask). 

<img width="1161" height="786" alt="image" src="https://github.com/user-attachments/assets/fdc6bfdc-bc70-44fe-9894-97dba8430112" />

The model consists of:
* Input layer L in
* Encoder block, consisting of 3 layers formed by the following elements:
  * Convolutional layer with a stride of (2, 2), which, in addition to its role as a convolutional layer, compresses the image due to the kernel stride
  * Activation function
  * Dropout
  * Convolutional layer
  * Activation function
  * Dropout
* The latent space, in this case, connects the encoder and decoder
* The decoder block consists of three layers containing:
  * Metoda UpSampling care are rolul de a mări dimensiunea imagini
  * Strat convolutiv
  * Funcție de activare
  * Dropout
  * Strat convolutiv
  * Funcție de activare
  * Dropout
* The output layer, in this case the output layer is a convolutional layer because it creates compatibility between the size of the data resulting from the previous layer and the annotation form. 




## Bibliographer:

https://www.geeksforgeeks.org/machine-learning/auto-encoders/

https://en.wikipedia.org/wiki/Autoencoder https://www.ibm.com/think/topics/autoencoder

https://www.geeksforgeeks.org/computer-vision/segnet-a-deep-convolutional-encoder-decoder-architecture-for-image-segmentation/

https://medium.com/@polanitzer/building-a-cnn-based-autoencoder-with-denoising-in-python-on-gray-scale-images-of-hand-drawn-digits-61131ec492e4

https://www.digitalocean.com/community/tutorials/convolutional-autoencoder

https://blog.roboflow.com/how-to-create-segmentation-masks-with-roboflow/

https://milvus.io/ai-quick-reference/what-is-a-mask-in-image-segmentation

https://www.digitalocean.com/community/tutorials/convolutional-autoencoder

https://keras.io/examples/vision/autoencoder/

https://docs.covalent.xyz/docs/user-documentation/tutorials/autoencoders/
