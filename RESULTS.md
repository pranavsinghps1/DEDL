# Results and Reproduction
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
|Swin Transformer Base (Patch 4 Window 12)     |0.891±0.0007|
|Vit-Base/16    |0.8426±0.007|
|Vit-Base/32      |0.8507±0.0079|
|Vit-large/16        |0.80495±0.0077|
|Vit-large/32       |0.845±0.0077|
