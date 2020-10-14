# Crop-Classification-With-Tensorflow

Transfer learning focuses on storing knowledge gained while solving one problem and applying it to another similar kind of problem. The same approach we used here with the OID Dataset with the pre-trained model of SSD MObileNet.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

NOTE- Before we start, I would like to tell you that the code is available as a google drive link due to ambiguity while uplaoding file size more than 25MB. For that, please visit the workspace folder! Also, you may have conflict while using Tensorflow version 2.0. So it is advisable to downgrade before using the repository.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

##  Phases in the process are-

### 1. Data Collection

- Basic part of any cycle where data plays a crucial role.
- Approx 250 raw-images are collected at initial level.
- Less data so we used Transfer Learning ideology.

###  2. Data Cleaning

- As this data is purely image based so we filter out the unrelevant data after scrapping data.
- These raw-images arec onverted into hybrid images manually for better classification purpose.
- In data cleaning, labeling of image is done as well with help of LabelImg tool.
- In the pre-porcessing stage the bounding box are converted into its values in the excel file where missing value and NaN value are treated by calculating the average of the     respective columns.

NOTE- LabelImg is freely available on github. Click on the link https://github.com/tzutalin/labelImg to have a look on the LabelImg.

###  3. Model Analysis

- Various models are available to deal with but we need to choose that one which limit our idea.
- For that, we choose SSDMobileNet because of its accuracy, i.e. 92.3% and scale of bounding box with label is (5,10).

###  4. Model Development

- Model is converted into tfrecord file which is basically a binary file understandable to machine only.
- During training, at regular intervals checkpoints are created, which contains all the necessary information regarding the model.
- Each step defines the loss at that particular stage, on-average a single step takes about 22.3 seconds.
- In total, 10,360 steps were taken in order to achieve an acceptable loss.
- If the loss gets less than 1.0000, there is a chance that model will get overfitted, so it’s better to stop the training.
- After each checkpoint is created, we can test the model by loading the frozen-inference graph.


###  5. Integrating in GUI

- Export of inference-graph leads to frozen_inferece_graph.pb file. Which can be used to load the saved model.
- With the help of single-image inference script, the graph is integrated with the GUI.
- GUI is developed on tkinter library of python.
- GUI has separate panels for the selection of inout file and dispaly of output file as shown below.

<img src="https://github.com/pranjalsharma26/Crop-Classification-Software/blob/main/Output/output_panel.JPG"/>

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Data Information

Data is splitted into train, test and valid directoreis and sample of annotation and data is available in those directories.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Process to start the workflow

### 1. Conversion

<img src="https://github.com/pranjalsharma26/Crop-Classification-Software/blob/main/Readme_Images/workflow.JPG"/>

### 2. Annotation

<img src="https://github.com/pranjalsharma26/Crop-Classification-Software/blob/main/Readme_Images/annotatio_view.JPG"/>

### 3. Training

- Training is the crucial stage where you need to tun the scripts in the training_demo folder.

##### Below are the few things to consider before you start training

- The simple error of starting the training from the zeroth step. That is strictly not allowed when it comes to Tensorflow 2.0 and its lesser version. So we changed it to the step at which the training was left on the parent model.

- While training it may happen that the tensorflow crashes because of either memory error or after each epoch it may give a warning that it increased the memory usage by 10%. That needs to be taken in consideration. If the warning occurs, stop the training immediately and decrease the batch size, or use the SGD for better efficiency.

- While using transfer learning, while resuming the training from the last trained step, do remember to have a fine-tune-checkpoint and detect-checkpoint variables defined, before starting the training steps.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
