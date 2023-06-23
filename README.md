# **Cell_Detect-Quantitative-Representation**

## ***AIM :***
  
-   ### **1. Cell Detection**
-   ### **2. CNN[Deep Learning] - Based Image Analysis for Quantitative Representation** 

  
 ## ***[Cell Detection](https://colab.research.google.com/github/Rajaguhan437/Cell_Detect-Quantitative-Representation/blob/main/Cell_Detection/Code/Cell_detect_Yolov5.ipynb) :***

-   ### Dataset : [90 Train + 10 val RBC/WBC Image Dataset with Annotation](https://www.dropbox.com/sh/v6epaau1kh7ofyj/AADOJsX-ghd70tn_ds1aDJtMa?dl=0). And chose to go with this dataset because there were no datasets with many different types of classes(cells) i.e, more than 3 or more with annotated data. 
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
        ###  Bounding Box Detections, Confidence Scores, Class of each cell are stored in this [Excel Sheet](Cell_Detection/Results/cell_data.xlsx) with the help pandas python library.

              
## ***CNN[Deep Learning] - Based Image Analysis for Quantitative Representation :***

-   ### **1. Cell Segmentation**
-   ### **2. Cell Image Quantitative Feature Extraction**

##  ***Cell Segmentation :***

-   ### **1. SAM Model**
-   ### **2. Yolov8-seg Model**
-   ### **3. Yolov5-det Model**


##  ***[SAM Model](https://colab.research.google.com/github/Rajaguhan437/Cell_Detect-Quantitative-Representation/blob/main/Cell_Image_Quantitative_Analysis/Segmentation/SAM-seg/SAM_seg.ipynb) :***

-  **[Segment Anything Model (SAM)](https://segment-anything.com/) : a new AI model from Meta AI that can "cut out" any object, in any image, with a single click
SAM is a promptable segmentation system with zero-shot generalization to unfamiliar objects and images, without the need for additional training.**

-  **Chose this Model because of its Zero-Shot Generalization and its performance.**

-  **SAM without any training segmnented the cells and the results were very good except the fact that it didn't segment WBCs.**

-  **So, thought of custom training but it was a very heavy process. So, chose to go with ***Yolo Family***.**

    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**Images**


    &emsp;&emsp;![Input Image](<Cell_Detection/Dataset/RBC_WBC-dataset/cells/images/train/image-1.png>) ![Segmented Output-Image](<Cell_Image_Quantitative_Analysis/Segmentation/SAM-seg/resized_segment_overlay.jpg>)


  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Input-Image&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Segmented-Masked Image
  
##  ***[Yolov8-seg Model](https://colab.research.google.com/github/Rajaguhan437/Cell_Detect-Quantitative-Representation/blob/main/Cell_Image_Quantitative_Analysis/Segmentation/Yolov8-seg/Yolov8_seg.ipynb) :***

-   **Introducing [Ultralytics YOLOv8](https://ultralytics.com/yolov8), the latest version of the acclaimed real-time object detection and image segmentation model. YOLOv8 is built on cutting-edge advancements in deep learning and computer vision, offering unparalleled performance in terms of speed and accuracy. Its streamlined design makes it suitable for various applications and easily adaptable to different hardware platforms, from edge devices to cloud APIs.**

-   **Super Fast with great accuracy and highly user friendly usage and docs.**

-   **Dataset : [2884 images with its segmented masks images which consists of 10 different type of classes(cells) such as Basophil, Eosinophil, Erythroblast, Intrusion, Lymphocyte, Monocyte, Myelocyte, Neutrophil, Platelet, RBC.](https://universe.roboflow.com/academie-militaire/oussama)**

-   **Started Custom Training, but the training time for yolov8-seg was so long that it took around 8:30 mins for each epoch which ultimately burned my google colab free gpu units.**

-   **So, now decided to go with already trained Yolov5-det model.**


##  ***[Yolov5-det Model](https://colab.research.google.com/github/Rajaguhan437/Cell_Detect-Quantitative-Representation/blob/main/Cell_Image_Quantitative_Analysis/Quantitaive_Analysis/code/yolov5_detseg.ipynb) :***
  
-   **Fast, precise and easy to train, [Ultralytics YOLOv5](https://ultralytics.com/yolov5) has a long and successful history of real time object detection. Treat YOLOv5 as a university where you'll feed your model information for it to learn from and grow into one integrated tool. With YOLOv5 and its  Pytorch implementation, you can get started with less than 6 lines of code.**

-   **With already custom trained yolov5-det model, the Bounding Box Detections, Confidence Scores, Class of each cell are computed and applied on the image.**  
    &emsp;&emsp;![Bounding Box on Each Cell](<Cell_Image_Quantitative_Analysis/Quantitaive_Analysis/output/each-cell.jpg>) 

-   **Then each cell are cropped to find its Quantitative Features.**  
    &emsp;&emsp;![Cropping the Bounded Box Area](<Cell_Image_Quantitative_Analysis/Quantitaive_Analysis/output/cropped-cell.jpg>)
    
##  ***[Cell Image Quantitative Feature Extraction](https://colab.research.google.com/github/Rajaguhan437/Cell_Detect-Quantitative-Representation/blob/main/Cell_Image_Quantitative_Analysis/Quantitaive_Analysis/code/yolov5_detseg.ipynb) :***

-   ### **1. Geometric Properties**
    -   Height
    -   Width
    -   Area
    -   Perimeter
    -   Aspect Ratio
    -   Major Axis
    -   Minor Axis
    -   Solidity
    -   Eccentricity
    -   Convexity
    -   Feret_Diameter
    -   Orientation
  
-   ### **2. Color Identification**
    -   RGB Values
    -   HEX Values
    -   Color Word
  
-   ### **3. Texture Properties**
  
-   ### **4. Intensity Properties**

     
-   ### All properties were computed using Computer Vision[cv2] & Scikit-Learn Python Libs.

  
-   ### All the above properties are stored in [Excel Sheet](Cell_Image_Quantitative_Analysis/Quantitaive_Analysis/output/cell_data.xlsx) with the help of pandas library. 


##  ***Note :***

-   ### Many of the codes were AI Generated through prompting.

-   ### But Detailed Description of how it's done can be traced back to my other repo python files such as [Segment Anything Model [SAM from META]](https://colab.research.google.com/github/Rajaguhan437/AI-Generation_SEGmnt/blob/main/Inpaint_Seg/SAM/code/Inpainting_SAM.ipynb) and [CLIP Model [from OpenAI]](https://colab.research.google.com/github/Rajaguhan437/AI-Generation_SEGmnt/blob/main/Inpaint_Seg/CLIP/code/Inpainting_CLIP.ipynb)


##  ***Extras :***

-  ### Google Colab Link for each Jupyter Notebook which enables instant accessing of the files.

    -  ### ***[Cell_detect_Yolov5.ipynb](https://colab.research.google.com/github/Rajaguhan437/Cell_Detect-Quantitative-Representation/blob/main/Cell_Detection/Code/Cell_detect_Yolov5.ipynb)***

    -  ###  ***[SAM_seg.ipynb](https://colab.research.google.com/github/Rajaguhan437/Cell_Detect-Quantitative-Representation/blob/main/Cell_Image_Quantitative_Analysis/Segmentation/SAM-seg/SAM_seg.ipynb)***

    -  ###  ***[Yolov8_seg.ipynb](https://colab.research.google.com/github/Rajaguhan437/Cell_Detect-Quantitative-Representation/blob/main/Cell_Image_Quantitative_Analysis/Segmentation/Yolov8-seg/Yolov8_seg.ipynb)***

    -  ###  ***[yolov5_detseg.ipynb](https://colab.research.google.com/github/Rajaguhan437/Cell_Detect-Quantitative-Representation/blob/main/Cell_Image_Quantitative_Analysis/Quantitaive_Analysis/code/yolov5_detseg.ipynb)***
    


 





        


        
      
           

