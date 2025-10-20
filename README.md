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
