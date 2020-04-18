# ArrythmiaDetection
ML project to detect abnormal heartbeats from ECG

The purpose of the project is to correctly classify heartbeats from ECG data as either "abnormal" or "normal". Specifically, "abnormal" heartbeats will refer to heartbeats with Arrythmia. From there, we want to apply several Machine Learning Interpretability algorithms to our models to see what features they are actually using to make their predictions.

Th project is split up into two parts: a MATLAB live script and a MATLAB AppDesigner application. 


The live script is fairly straightforward. The first half of the script is mainly preparing the raw data from the MIT-Databases for Arrythmia and Normal Heartbeats. The data can be downloaded here:
https://www.physionet.org/content/mitdb/1.0.0/
https://www.physionet.org/content/nsrdb/1.0.0/

Please note that in order to work with the data gleaned from the database, you must downloaded the WFDB toolbox. It is a 3rd party toolbox found here:
https://archive.physionet.org/physiotools/matlab/wfdb-app-matlab/

I perused a few academic papers that had already tackled this problem and decided to go with 8 features. I chose them for their simplicity and for their reputation as powerful indicators of abnormal vs normal heartbeats. They are as follows:

1. The interval between beat n-2 and beat n-1
2. The interval between beat n-1 and beat n
3. The interval between beat n and n + 1
4. The ratio of feature (1) over feature (2)
5. The ratio of feature (3) over feature (2)
6. The mean of features 1 to 3, divided by feature (2)
7. The amplitude of beat n (channel 1)
8. The amplitude of beat n (channel 2)


The live script then trains several machine learning models, a single decision tree, Gaussian SVM, and a random forest. We get 85, 92, and 96% accuracy respectively, proving the adage that more complicated models are more accurate, but less interpretable. The follwoing two interpretability methods are then applied to the models: PDP/ICE for classification and LIME.

The live script concludes there. However, to augment the project, I also created an app in AppDesigner.
It allows you to load any model you want, and then customize your variable names. It has custom labels describing what the features are specific to ECG data. Finally, there are many available drop downs to help customize the way you want your PDP/ICE/LIME graphs to look. 

HOW TO RUN:
First start with the live-script: "ECG Classification.mlx". Feel free to skip all of the data-preprocessing steps and load the .MAT files directly. They are located in the folder "MAT Files". From there, head on over to the visualizeECG application and load your trained model and test sets (these will also be loacated in the folder "MAT Files"). 

If you want to work with the raw data from the Databases, please download from the links referenced above. 
