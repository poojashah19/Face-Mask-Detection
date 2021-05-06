1. Preparing data
	Downloaded images from https://www.kaggle.com/andrewmvd/face-mask-detection link. I also downloaded around 100 images without mask as the data has lesser number of images with no mask.

2. Image Transformation
	I rescaled the images in a standard size of 800*600

3. Image Labeling
	I labeled the data manually using LabelImg, which generates an xml file respective of an image that contains size, label name, xmin, xmax, ymin, and ymax. This process of labeling needs to be repeated for all the images

4. Transform into csv
	After labeling all the images, we will combine all of the xml files into a csv file.

5. Generating TFRecords
	We need TFRecord file which we will provide as an image to the model for training. A TFRecord file stores the image data in a sequence of binary strings. For that we will input csv file generated in previous step. Edit generate_tfrecords.py file, add all the class labels in class_text_to_int method and record file is generated using below command

python generate_tfrecord.py --csv_input=images/train_labels.csv --image_dir=images/train --output_path=train.record

6. Configuration for training
	Create a labelmap text file and add items that are named as class labels, check labelmap.pbtxt. Select a model of your choice from https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf1_detection_zoo.md page. Go to config file and make changes as required. Check the training notebook file

7. Train Model and check for loss graph on Tensorboard.

8. Export inference_graph

9. Test Model

I achieved loss of 0.35 and accuracy of with mask 

Credits:
https://gilberttanner.com/blog/creating-your-own-objectdetector
