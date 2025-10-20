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


## Dataset Training
The training data consists of 3 RGB images with dimensions of 1024X512X3 and 3 annotations with binary values with dimensions of 1024X512x1.

<img width="640" height="480" alt="image" src="https://github.com/user-attachments/assets/5852b8d9-4ebf-422d-81aa-50e2b6ee8f89" />

## Loss function graph

The graph shows the decrease in the loss function value in relation to the evolution of iterations (Epocs). If there is a significant increase in the loss function value returned by the validation data, in relation to the loss function values returned by the training data, the model overfits.

<img width="1000" height="600" alt="image" src="https://github.com/user-attachments/assets/0c912e54-43c0-4bad-a98a-cd4579215fa0" />

## Evolution of predictions during training

For a better visualization of the learning process, you can observe the evolution of the prediction of the 3 training data points. 

<img width="2000" height="1000" alt="image" src="https://github.com/user-attachments/assets/28066f82-9326-46af-a30f-e8f48563c884" />

## The graph reflecting the model performance

<img width="1000" height="600" alt="metric" src="https://github.com/user-attachments/assets/381bceee-6ef0-49cf-bef6-cf9e74850150" />

## Comparison between predictions and reality

<p align="center">
<img width="500" height="774" alt="image" src="https://github.com/user-attachments/assets/8fbfd7bf-6162-4f49-b6ad-08b514463833" />  
</p> 
<p align="center">
<img width="399" height="762" alt="image" src="https://github.com/user-attachments/assets/3bc564b1-2fe6-4ba5-a5bf-35a782143fed" />
</p>
<p align="center">
<img width="393" height="759" alt="image" src="https://github.com/user-attachments/assets/95d9e8fa-b30b-4672-add1-0f9659a494aa" />  
</p>
<p align="center">
<img width="395" height="748" alt="image" src="https://github.com/user-attachments/assets/46899a7e-c308-447c-9004-66ab6fa98ddc" />
</p>
<p align="center">
<img width="408" height="756" alt="image" src="https://github.com/user-attachments/assets/758efdfc-7b77-43a0-bc96-31261d81a494" />
</p>



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
