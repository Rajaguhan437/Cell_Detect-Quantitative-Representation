# **Cell_Detect-Quantitative-Representation**

## ***AIM :***
  
-   ### **1. Cell Detection**
-   ### **2. CNN[Deep Learning] - Based Image Analysis for Quantitative Representation** 

  
 ## ***Cell Detection :***

-   ### Dataset : [90 Train + 10 val RBC/WBC Image Dataset with Annotation](https://www.dropbox.com/sh/v6epaau1kh7ofyj/AADOJsX-ghd70tn_ds1aDJtMa?dl=0)
    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Sample Image


    &emsp;&emsp;![Input Image](<Cell_Detection/Dataset/RBC_WBC-dataset/cells/images/val/image-23.png>) ![Annotated Label-Image](<Cell_Detection/Dataset/RBC_WBC-dataset/Sample annotated image/annotated_image-23.png>)


  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Input-Image&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Annotated-Labelled Image

-  ### Object-Detection Model : Custom Trained **[Yolov5](https://github.com/ultralytics/yolov5)**
  

-  ### Training Output :
    -   1.  
        ### Trained Model-Weights on 300 Epochs : [Click Here](Cell_Detection/Results/rbcd/weights)
        
    -   2.  
          ![Yolo_Layers](<Cell_Detection/Results/yolo_layers.png>)
  
    -   3.  
          ![Yolo_val_detect](<Cell_Detection/Results/yolo_val_dect.png>)

    -   4.
        ###  Bounding Box Detections, Confidence Scores, Class of each cell are stored in this [Excel Sheet](Cell_Detection/Results/cell_data.xlsx)

              
## ***CNN[Deep Learning] - Based Image Analysis for Quantitative Representation :***

-   ### **1. Cell Segmentation**
-   ### **2. Cell Image Quantitative Feature Extraction**

##  ***Cell Segmentation :***

-   ### **1. SAM Model**
-   ### **2. Yolov8-seg Model**
-   ### **3. Yolov5-det Model**


##  ***SAM Model :***

-  **[Segment Anything Model (SAM)](https://segment-anything.com/) : a new AI model from Meta AI that can "cut out" any object, in any image, with a single click
SAM is a promptable segmentation system with zero-shot generalization to unfamiliar objects and images, without the need for additional training.**

-  **Chose this Model because of its Zero-Shot Generalization and its performance.**

-  **SAM without any training segmnented the cells but the results were very good except the fact that it didn't segment WBCs.**

-  **So, thought of custom training but it was a not a easy process. So, chose to go with Yolo Family.**

    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**Image**


    &emsp;&emsp;![Input Image](<Cell_Detection/Dataset/RBC_WBC-dataset/cells/images/train/image-1.png>) ![Annotated Label-Image](<Cell_Image_Quantitative_Analysis/Segmentation/SAM-seg/segment_overlay.jpg>)


  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Input-Image&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Annotated-Labelled Image



 





        


        
      
           

