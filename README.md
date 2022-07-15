# A Data-Efficient Deep Learning Framework for  Segmentation and Classification of  Histopathology Images

Official PyTorch implementation of the following paper: [ A Data-Efficient Deep Learning Framework for Segmentation and Classification of Histopathology Images](https://arxiv.org/abs/2207.06489). arXiv 2022.


# Description of the mathematical models

We provide code for classification and segmentation on the Whole slide Histopathology Images of biopsies of dermatomyositis. For Segmentation, we tested algorithms using U-Net and U-Net++ architectures and our Novel Autoencoder Post Processing (APP) architecture. APP Improves performance upon traditional segmentation techniques by an average of 3% for UNet and Unet++ with Resnet Family (Refer Section 5.1 of Paper) of Encoder and 5% for Efficient net family of encoders (Refer Section 1.2 of Supplementary material of Paper).

For Classification, we have tested our proposed approach on CNNs and Transformers; a complete list of all results can be found in section 5.2.

## Assumptions

We don't account for any meta-data. 
 

## Dataset

We developed and tested our approach on a private dataset consisting of biopsies of dermatomyositis. This dataset has also been used by [Van Buren et al.] [1]

### Segmentation

We use the same splits as mentioned in [Van Buren et al.] [1]

### Classification 

We split the dataset in 80/20 for training and testing. Within the training set, we perform a 6-fold cross-validation.

### Dataset description

The dataset we used contained 198 tiff image sets containing eight slide images per tiff image. These eight slide images had different protein staining DAPI, CXCR3, CD19, CXCR5, PD1, CD4, CD27 and autofluorescence. The DAPI stained slides were used for image segmentation. These are black and white images with sizes 1408 and 1876. For classification, we use the autofluorescence slides, which contain all the phenotype labels from CXCR3, CD19, CXCR5, PD1, CD4, and CD27. Autofluorescence slides are 352 by 469 in RGB.

## Specification of dependencies

Run the following commands to make sure all dependencies are installed. (Latest version recommended)
`pip install pytorch_lightning`
`pip install torchcontrib`
`pip install torchmetrics`
`pip install -U git+https://github.com/qubvel/segmentation_models.pytorch`
`pip install timm`
`pip install tqdm`

NOTE: segmentation_models.pytorch installs an older version timm package for itself, which might break some part of the code. So, it is better to uninstall that and install the latest version of timm (version 0.5 and beyond).

We assume that the practitioner has a working installation (latest recommended) of Pytorch, Numpy, matplotlib and pandas.

<<<<<<< Updated upstream
## Result Reproduction

All the jupyter notebooks contain sequence code for training and testing the trained models.  

## Segmentation Results

In the following two tables, we compare the IoU score on the test set, averaged over five runs.


### Segmentation results for UNet with and without the Autoencoder post-processing(APP).
|    Encoder            |Without APP                         |With APP (GELU)                       |
|----------------|-------------------------------|-----------------------------|
|Resnet-18|0.4347±0.0006    |**0.4788±0.0004**      |
|Resnet-34         |0.4774±0.0004          |**0.4983±0.0008**          |
|Resnet-50         |0.3798±0.00072|**0.3827±0.0003**|
|Resnet-101         |0.3718±0.0001|**0.4402±0.00018**|
|Efficientnet-B0        |0.3785±0.00061|**0.4282±0.0008**|
|Efficientnet-B1          |0.3301±0.0002|**0.4237±0.0006**|
|Efficientnet-B2          |0.2235±0.0007|**0.3735±0.0009**|
|Efficientnet-B3         |**0.3982±0.0007**|  0.2411±0.0004|
|Efficientnet-B4          |0.3826±0.0004|**0.3829±0.0006**|
|Efficientnet-B5          |0.4056±0.0008|**0.4336±0.0008**|
|Efficientnet-B6          |0.4001±0.0001|**0.4311±0.0006**|
|Efficientnet-B7          |0.3631±0.0002|**0.3937±0.0004**|

### Segmentation results for UNet++ with and without the Autoencoder post-processing(APP).
|    Encoder            |Without APP                         |With APP (GELU)                       |
|----------------|-------------------------------|-----------------------------|
|Resnet-18|**0.5274±0.0004**   |0.4707±0.00067     |
|Resnet-34         |0.3745±0.0006         |**0.4678±0.0004**         |
|Resnet-50         |0.4236±0.0004|  **0.4422±0.0007**|
|Resnet-101         |0.4311±0.0003|**0.4467±0.0003**|
|Efficientnet-B0        |0.3584±0.0002|**0.3751±0.0007**|
|Efficientnet-B1          |0.4260±0.0005|**0.4269±0.0003**|
|Efficientnet-B2          |0.3778±0.0007|**0.3942±0.0009**|
|Efficientnet-B3         |0.3928±0.0006|  **0.4174±0.0003**|
|Efficientnet-B4          |0.4138±0.0003|**0.4273±0.0002**|
|Efficientnet-B5          |**0.3884±0.0001**|0.3875±0.0005|
|Efficientnet-B6          |0.4090±0.0008|**0.4214±0.0007**|
|Efficientnet-B7          |0.3784±0.0009|**0.4002±0.0005**|



## Classification Results

|    Encoder            |Classification F1 Score                         |
|----------------|-------------------------------|
|Resnet-18|0.8635±0.0087  |
|Resnet-34         |0.82765±0.0073       |
|Resnet-50         |0.8499±0.007| 
|Resnet-101         |0.871±0.009|
|Efficientnet-B0        |0.8372±0.0007|
|Efficientnet-B1          |0.8346±0.0026|
|Efficientnet-B2          |0.828±0.00074|
|Efficientnet-B3         |0.8369±0.0094|  
|Efficientnet-B4          |0.8418±0.0009|
|Efficientnet-B5          |0.8463±0.00036|
|Efficientnet-B6          |0.8263±0.00147|
|Efficientnet-B7          |0.8129±0.001|
|nfnet-f0          |0.82035±0.007|
|nfnet-f1         |0.834±0.007|
|nfnet-f2          |0.8652±0.0089|
|nfnet-f3         |0.8898±0.0011|
|nfnet-f4         |0.8848±0.0109|
|nfnet-f5        |0.8161±0.0074|
|nfnet-f6        |0.8161±0.0074|
|ConvNext-tiny       |0.81355±0.0032|
|ConvNext-small       |0.84795±0.00246|
|ConvNext-base        |0.80675±0.002|
|Swin Transformer large (Patch 4 Window 12)   |0.8839±0.001|
|Swin Transformer Base (Patch 4 Window 12)     |**0.891±0.0007**|
|Vit-Base/16    |0.8426±0.007|
|Vit-Base/32      |0.8507±0.0079|
|Vit-large/16        |0.80495±0.0077|
|Vit-large/32       |0.845±0.0077|


# Time Complexity Comparison with and without APP 

For segmentation, APP is only used during training. This increases the training time marginally  (more details in supplementary material section 1.2). But the size of saved model weights and inference time remains constant. 

=======
>>>>>>> Stashed changes
# Explore the files


- DEDL/ Segmentation with APP/Semantic Segmentation with APP.ipynb contains the training code for Training segmentation architecture with Autoencoder post-processing.

	At the bottom it also has helper function for testing the results on Test set.

	For changing the segmentation architecture:
	`import segmentation_models_pytorch as smp`
	`model = smp.Unet(encoder_name=encoder_name,......`
 This model is currently using UNet architecture, to chnage to Unet++ simply change Unet to Unetplusplus. For more details check the complete list of supported architecture by `segmentation_models_pytorch`.
 Note: we have only tested on Unet an Unet++ architectures.

- DEDL/ Segmentation with APP/Semantic Segmentation.ipynb contains the segmentation architecture with the post-processing autoencoder architecture (APP). This notebook also contains the testing code at the bottom. Similarly, segmentation architecture can be changed as mentioned in the above step.

- DEDL/Classification/Supervised.ipynb contains the code for supervised classification of the given dataset. This algorithm has been tested for CNNs and Transformers supported by timm. To test the saved models, use the code provdied in DEDL/Classification/Testing.ipynb 

## Results & Reproduction

See [RESULTS.md](RESULTS.md) for more details.

# Time Complexity Comparison with and without APP

For segmentation, APP is only used during training. This increases the training time marginally  (more details in supplementary material section 1.2). But the size of saved model weights and inference time remains constant.



# References

-   `[1]: https://www.sciencedirect.com/science/article/abs/pii/S0022175922000205`
- segmentation_models.pytorch: https://github.com/qubvel/segmentation_models.pytorch
- Timm encoders/CNNs and Transformer Implementation for Pytorch: https://github.com/rwightman/pytorch-image-models

# Citation

```
@misc{https://doi.org/10.48550/arxiv.2207.06489,
  doi = {10.48550/ARXIV.2207.06489},
  
  url = {https://arxiv.org/abs/2207.06489},
  
  author = {Singh, Pranav and Cirrone, Jacopo},
  
  keywords = {Image and Video Processing (eess.IV), Computer Vision and Pattern Recognition (cs.CV), Machine Learning (cs.LG), FOS: Electrical engineering, electronic engineering, information engineering, FOS: Electrical engineering, electronic engineering, information engineering, FOS: Computer and information sciences, FOS: Computer and information sciences},
  
  title = {A Data-Efficient Deep Learning Framework for Segmentation and Classification of Histopathology Images},
  
  publisher = {arXiv},
  
  year = {2022},
  
  copyright = {Creative Commons Attribution 4.0 International}
} 
```

