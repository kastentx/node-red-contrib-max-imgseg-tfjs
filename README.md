node-red-contrib-max-imgseg-tfjs
=====================

This contains the Node-RED node `node-red-contrib-max-imgseg-tfjs` which uses the [MAX Image Segmenter](https://github.com/IBM/MAX-Image-Segmenter) deep learning model from the [Model Asset eXchange (MAX)](https://developer.ibm.com/exchanges/models/).

About the model:
----------------

This model takes an image file as an input and returns a segmentation map containing a predicted class for each pixel in the input image.

This repository contains 2 models trained on PASCAL VOC 2012. One model is trained using the xception architecture and produces very accurate results but takes a few seconds to run and the other model is trained on MobileNetV2 and is faster but less accurate. You can specify which model you wish to use when you start the Docker image. See below for more details.

The segmentation map returns an integer between 0 and 20 that corresponds to one of the labels below for each pixel in the input image. The first nested array corresponds to the top row of pixels in the image and the first element in that array corresponds to the pixel at the top left hand corner of the image. NOTE: the image will be resized and the segmentation map refers to pixels in the resized image, not the original input image.


Install
-------

To install this node into your Node-RED environment, first clone this repo and run the command `sudo npm link`. This will create a symlink which makes it available to Node-RED.

Alternatively, you can clone this repo directly into `./node-red/node_modules/` (assuming the default install location) and then run `npm install` from within the directory created by this repo to install the required dependencies.

Usage
-----

The node accepts a buffer containing image data and will return a predicted segmentation map and a list of the different objects detected. For more information on the response from the model, see the [model's documentation](https://developer.ibm.com/exchanges/models/all/max-image-segmenter/).
