# Scene Classification using Unsupervised Learning

>*NOTE: Data is NOT included in this repository.

![Examples of frames of 3 distinct scenes](http://i.imgur.com/IZZeoBf.jpg)

This notebook contains a method for classifying keyframes from camera feeds using unsupervised learning through clustering.  The user only needs to specify into how many scenes the frames will be classified.  The KMeans algorithm compares flattened bilevel histograms of patches of the frames.  An illustration of the routine follows.

### Software and Library Requirements
* Python 2.7.11
* Jupyter Notebook 4.2.2
* Numpy 1.11.2
* PIL Image 1.1.7
* scikit-image 0.12.3
* matplotlib 1.5.2

## Goals
This repository demonstrates a novel solution to classify a directory of keyframes (images) from a PTZ camera according to unique "scene" through unsupervised learning techniques.  Analysis allows the user to view plots of clustering behavior, as well as to identify the frames that are most-difficult to categorize.

## Key Processes
1. Classify directory of scenes
2. Analyze classification behavior

## Routine & Illustration
1. User selects size of fixed tiles according to imagery features (e.g. 80 x 80 pixels).
![Fixes tiles of size 80x80 pixels](http://i.imgur.com/VOhYXWe.jpg)

2. User selects a ROI in the frame that will be compared across all frames (e.g. tiles 32 to 79 have been chosen here to capture the location of the jetty in the feed).
![ROI](http://i.imgur.com/H0mvs6F.jpg)

3. User defines number of unique scenes from empirical evidence.

4. Program will crop scene to ROI and desaturate image according to the ITU-R 601-2 luma transform.
![Cropped frames](http://i.imgur.com/slProXZ.jpg)

5. Program will "equalize histogram" of greyscale intensity values across entire ROI.
![Equalized frames](http://i.imgur.com/lTvFOH2.jpg)

6. User selects a threshold to compare bilevel histograms (e.g. 20, 80, or 120)
![Thresheld images](http://i.imgur.com/HtY2Y4K.jpg)

7. Program will calculate bilevel histograms for all tiles in the ROI for the frame according to user-defined threshold.
![Threshold image](http://i.imgur.com/0nzLr2Y.jpg)

8. Program will flatten all histograms in a frame sequentially, ensuring that spatial information about the image is preserved during clustering.

9. Program will attempt to cluster the frames into the number of scenes defined by the user, using the Euclidean distance metric to evaluate similarity of the flattened spatial histograms across all frames.

10. Program will return labels of all the frames.

Analysis steps allow the user to view plots of clustering behavior, as well as to identify the frames that are most-difficult to categorize.

## Code Organization

File | Purpose
------------ | -------------
sceneclustering.ipynb |	iPython Notebook for clustering routine.

## Getting up and running

While in the `sceneclustering` directory, enter the following in the command line:

> ipython notebook sceneclustering.ipynb
