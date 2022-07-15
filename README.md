# A Data-Efficient Deep Learning Framework for  Segmentation and Classification of  Histopathology Images

Official PyTorch implementation of the following paper: [ A Data-Efficient Deep Learning Framework for Segmentation and Classification of Histopathology Images](https://arxiv.org/abs/2207.06489). arXiv 2022.

[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/a-data-efficient-deep-learning-framework-for/medical-image-segmentation-on-autoimmune)](https://paperswithcode.com/sota/medical-image-segmentation-on-autoimmune?p=a-data-efficient-deep-learning-framework-for)
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/a-data-efficient-deep-learning-framework-for/classification-on-autoimmune-dataset)](https://paperswithcode.com/sota/classification-on-autoimmune-dataset?p=a-data-efficient-deep-learning-framework-for)

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

