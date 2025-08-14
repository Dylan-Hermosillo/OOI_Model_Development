# Global Irminger Ice Detection Model (and clouds)
[Dylan Hermosillo](https://github.com/Dylan-Hermosillo) - OOI Guest Student (CI:Compass)
Hermosillodylan@gmail.com / Dhermos@NCSU.edu

This project works with the image stills generated from the mooring cameras on the suface buoy in the GI sea array. Raw files are downloaded, and clustered with ViT tools to generate image data to train and test a model for ice/cloud detection using a convolutional neural network.

## Notebook 1 -- Data Collection

Raw data is available on the public OOI data repository. The notebook contains links to the publicly available directories for image stills. Photos are pulled directly from the server. Certain camera angles are for viewing the machinery and are not useful for model development; this notebook filters them out by camera name suffix.

## Notebook 2 -- Unsupervised Clustering

The goal of this project is to develop a CNN ice floe model. We need training/testing data, therefore we need to find ice images. This notebooks alleviates the manual sorting of ~300k images by using DinoV2 (a visual transformer) to classify the images for easier manual processing. 

## Notebook 3 -- Image Similarity Search

A reference ice floe photo was the kickstarter for this project. Using this image and a similarity search library toolkit, this notebook ranks images by similarity of photo embeddings (numerical represenations of the pixels) to further process the image stills for manual processings.

## Notebook 4 -- Summer Timeframe Search

Ice floe season in the North Atlantic exists when glaciers/ice features melt and breakoff into the ocean. This notebook worked to isolate images during this specific timeframe using datetime formats embedded in the image file names. After, images can be manually processed or Notebook 2/3 can be run to cluster using ViT's or similarity search algorithms.

## Notebook 5 -- Model development

With the abundance of cloud image stills a model can be developed to parse through the photos. After manually annotating photos derived from notebooks 2-4, the data was uploaded and a CNN model was developed using PyTorch.

## Future Work -- Annotations & Better Training/Testing Set

Some considerations for future work; the model has a decent loss score after enough epoch training runs. A larger test set could help tease out the differences between cloud density (if needed -- this could be a binary cloud vs no cloud model). Additional considerations can include feature detection (ship vs bird).

Additionally, the model can be applied on non-cloud images to sort out stills that aren't useful to the project scope (in-harbour shots, night time photos or image stills taken with sea-spray on the lens).

## Useful Links / resources

[DinoV2 -- Explanation/Demo](https://dinov2.metademolab.com/)

[DinoV2 Repository](https://github.com/facebookresearch/dinov2)

[FAISS](https://github.com/facebookresearch/faiss)

[Article 1 (DinoV2 & FAISS)](https://medium.com/aimonks/image-similarity-with-dinov2-and-faiss-741744bc5804)

[Article 2 (CLIP & FAISS)](https://medium.com/aimonks/image-similarity-with-dinov2-and-faiss-741744bc5804)

[PyTorch: Training a Classifier](https://docs.pytorch.org/tutorials/beginner/blitz/cifar10_tutorial.html)