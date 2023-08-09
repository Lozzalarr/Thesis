TODO: 
- add the tile fixing script and clean it up 
- fix enviro.yaml file to work and for future to allow:
    - opencv-python
    - vrpy

# Deep learning and FMV in Arcgis from Roboflow

The purpose of this repository is to convert annotations from [Roboflow](https://roboflow.com/) into ESRI reading deep learning folders to be use ArcGIS pro/Arcgis Enterprise/Arcgis Online Notebooks.

This requires the exported annotations from roboflow to be in PASCAL VOC format.



Use the sample data to test the notebooks and get familiar or go straight to using your own data from Roboflow.

## Install the Required Dependenices

Open Anaconda prompt and change directory to repository folder with this code:

```cd /path/to/repository```


install dependencies with conda using the enviro.yaml file     

```conda env create -f enviro.yaml```

## Convert Roboflow to ESRI

Scripts:
- Convert_PASCAL_OneClass.ipynb
- Convert_PASCAL_TwoClass.ipynb 

### Multiple Classes

depending on the amount of classes you have you can use these two notebooks to prepare Roboflow annotations into ESRI ready deep learning annotations.

If you have more than two classess, you can adjust cell 3 in the notebooke and include more classes.

                elif '<name>{}</name>'.format(class_name) in line:
                    sys.stdout.write(line.replace('<name>{}</name>'.format(class_name), '<name>{}</name>'.format(class_value)))
                # Replace Surfer standing with 2
                elif '<name>{}</name>'.format(class_name2) in line:
                    sys.stdout.write(line.replace('<name>{}</name>'.format(class_name2), '<name>{}</name>'.format(class_value2)))

simply duplicate the second elif statement and add additional classnames and classvalues at the top of the cell to fit for your classess.

### ESRI files to fill

You can find in the ESRI_Templates folder three files:

- esri_accumulated_stats.json
- esri_model_definition.emd
- stats.txt

use the notebooks to fill out these files correctly.

inside the files will be '##' in lines that need to be filled. 

## Additonal notebooks

- mIoU_calculations.ipynb
    - using the detected tracks and the ground truth, produce the Intersection of Union calculations 
- distance_calculations.ipynb
    - calculate the offset distances for each point at each point in time for the detections and the ground truth tracks. requires the point locations of the detections and the FMV point annotations before the line segments are generated.

