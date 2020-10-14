## H1 Crop-Classification-With-Tensorflow

Transfer learning focuses on storing knowledge gained while solving one problem and applying it to another similar kind of problem. The same approach we used here with the OID Dataset with the pre-trained model of SSD MObileNet.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## H2  Phases in the process are-

## H3 1. Data Collection

- Basic part of any cycle where data plays a crucial role.
- Approx 250 raw-images are collected at initial level.
- Less data so we used Transfer Learning ideology.

## H3 2. Data Cleaning

- As this data is purely image based so we filter out the unrelevant data after scrapping data.
- These raw-images arec onverted into hybrid images manually for better classification purpose.
- In data cleaning, labeling of image is done as well with help of LabelImg tool.
- In the pre-porcessing stage the bounding box are converted into its values in the excel file where missing value and NaN value are treated by calculating the average of the     respective columns.

NOTE- LabelImg is freely available on github. Click on the link https://github.com/tzutalin/labelImg to have a look on the LabelImg.

## H3 3. Model Analysis

- Various models are available to deal with but we need to choose that one which limit our idea.
- For that, we choose SSDMobileNet because of its accuracy, i.e. 92.3% and scale of bounding box with label is (5,10).

## H3 4. Model Development

- Model is converted into tfrecord file which is basically a binary file understandable to machine only.
- During training, at regular intervals checkpoints are created, which contains all the necessary information regarding the model.
- Each step defines the loss at that particular stage, on-average a single step takes about 22.3 seconds.
- In total, 10,360 steps were taken in order to achieve an acceptable loss.
- If the loss gets less than 1.0000, there is a chance that model will get overfitted, so it’s better to stop the training.
- After each checkpoint is created, we can test the model by loading the frozen-inference graph.


## H3 5. Integrating in GUI

- Export of inference-graph leads to frozen_inferece_graph.pb file. Which can be used to load the saved model.
- With the help of single-image inference script, the graph is integrated with the GUI.
- GUI is developed on tkinter library of python.
- GUI has different panels for the selection of inout file and dispaly of output file.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
