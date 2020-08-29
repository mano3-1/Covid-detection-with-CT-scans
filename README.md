# Covid-detection-with-CT-scans
The aim of this project is to detect covid-19 from images of CT-Scans. As we all know, we are currently facing this covid-19 pandemic and since it is hard to be detected, the situation is becoming worst day by day. So, with the help of powerful deep learning algorithms like CNNs for classification and image segamnetation, we designed an model which could potentially classify whether a patient have covid-19 infection or not by just taking CT-scan as input! We are making this as an open sourced repository so that any valuable asserts such as more data, new algorithms or new techniques can be added to it!<br/>
## About Data:
Data was collected from various repositories and hospitals. Since it is collected from various sources, due to the differences in the x-ray machine from which they are obtained, it was really hard to train a CNN model which could yield as good accuracy. So, we used segmentation as the preprocessing technique to extract the Region of Interest(ROI) of the given image and fed it to a classifier.
## About Segmentation model:
We used BCD U-net for segmentation. It was pretrained on the large open-sourced kaggle lung-segmentation dataset and with the help of transfer learning, we used this model to perform the basic preprocessing which was discussed in earlier section.<br/>
!['Segmenation_results](https://github.com/mano3-1/Covid-detection-with-CT-scans/blob/master/Results/segmentaion_results.png)
## Architecture:
We framed the problem as binary classification and trained an EfficientNetB0(with a CNN head on top of it) for classifying the CT-scans. SInce, we have encountered some class imabalance in early stages of collecting data, we have used focal loss to deal with it. The mask is obtained from the segmentation model and multiplied with the original image to extract the region of interest from the source image. Now, these preprocessed images are sent into classifier for final classification.<br/>
!['Training Pipeline'](https://github.com/mano3-1/Covid-detection-with-CT-scans/blob/master/Results/pipeline.png)

## Training curves:
!['Loss'](https://github.com/mano3-1/Covid-detection-with-CT-scans/blob/master/Results/loss.png) 
!['accuracy'](https://github.com/mano3-1/Covid-detection-with-CT-scans/blob/master/Results/acc.png)

## Results:
Our model after training for 30 epochs in google colab, has achieved an accuracy of 80.6%. Other metrics are give below.<br/>
Accuracy  : 80.6% <br/>
F1 Score  : 0.823 <br/>
Recall    : 0.848 <br/>
Precision : 0.800 <br/>
ROC AUC   : 0.806 <br/>
