---
layout: default
title: Classification of 2 Classes (With or Without Tumor)
parent: Problems
nav_order: 1
---

# Classification of 2 Classes (With or Without Tumor)
{: .no_toc }


## 1. INTRODUCTION

The process of diagnosing brain tumors from magnetic resonance imaging (MRI) is often time-consuming. Thus, a rapid analyses through an automated system could help improve the treatment possibilities and optimize hospital resources. The following neural network classifies MRI images as tumoral and non-tumoral.

## 2. MATERIALS AND METHODS
### 2.1 BRATS2020 Dataset

We conducted our experiments using the data available in the Multimodal Brain Tumor Segmentation Challenge 2020 (BRATS2020) dataset [17]. The BRATS2020 dataset has images of MRI scans and describe a) native (T1), b) post-contrast T1-weighted (T1Gd), c) T2-weighted (T2), and d) T2 Fluid Attenuated Inversion Recovery (T2-FLAIR) volumes. The images were acquired from 371 patients, using diff erent clinical protocols and various scanners from 19 institutions. For each patient, there are four MRI 3D scans. The images have been manually segmented, by one to four raters, following the same annotation protocol. Annotations comprise the GD-enhancing tumor (ET — label 4), the peritumoral edema (ED — label 2), and the necrotic and non-enhancing tumor core (NCR/NET — label 1). In the present study, 8,099 axial 2D MRI slices were extracted from the 3D MRI flair images. The slices were randomly extracted and the masks were used only to indicate the presence of a brain tumor in each slice. Among the 8,099 2D MRI scans, 3,999 scans (49.4%) contain tumors and 50.6% do not, providing a balanced dataset.

## 3. CNN BRAIN TUMOR DETECTION MODEL

To identify if an image has a tumor, we used a CNN-based classification system. More specifically, we considered the Resnet18 architecture. While training the architecture, we used the cross-entropy as the loss function and Adam as the optimizer. We considered batches of 64 sub-images with a default *learning rate* of 0.002. All evaluated architectures were pre-trained, using weights imported from the *Imagenet* dataset. The last layer of the network was trained using the BRATS2020 dataset (for a dataset description, see Section 2.1. To perform this training, we used 80% of the images for training and 20% of the images used for test. As mentioned earlier, each of these subsets contains approximately 50% of the images with tumors and the remaining 50% of the images without tumors. The patients from the training set were different from those in test set. To avoid any bias in the dataset split, a 𝑘 -fold was used with 𝑘 = 10. The results are presented in the next section.

## 4. RESULTS

### 4.1 Original Images
The results for classifying the existence or not of a tumor are given by the table and by the confusion matrix, Figure [1], shown below.

![Results_Original](https://user-images.githubusercontent.com/43020938/154950112-37b25b78-1bda-4d0a-8df7-731b9cc31dc2.PNG)

![CM_original_images](https://user-images.githubusercontent.com/43020938/154949534-c08ef5a1-de39-42b3-8aea-6e8b46fae8f4.png)

 In Figure [2], the heatmap of an image sample indicates the most discriminative parts used by the resnet18 for classification. The areas with red color were the ones that had the greatest weight in the network decision and the areas closest to blue were the least significant regions.

![Heatmap_original_image](https://user-images.githubusercontent.com/43020938/154948876-aba9e571-3df8-4ed2-93fd-8a2f7c1189cd.png)

### 4.2 Images with Noise
Below are examples of images with different noise levels:
![Noisy_Images](https://user-images.githubusercontent.com/43020938/156930924-ff2a0a70-d7f0-4bc4-b72c-3b2dcdb5838a.png)

The following table contains the classification results after adding gaussian noise to the images:


### 4.3 Images with Blur
Below are examples of images with different blurring levels:
![Blur_Images](https://user-images.githubusercontent.com/43020938/156930936-611fb586-b6f9-43db-afa4-2a2f6e1eb58e.png)

The following table contains the classification results after blurring the images:

### 4.4 Images with Contrast
Below are examples of images with different contrast levels:
![Contrast_Images](https://user-images.githubusercontent.com/43020938/156930945-afb82f87-55f0-4c78-ba78-d9a9a37b65d6.png)

The following table contains the classification results after changing contrast effect to images:

### 4.5 Images with Ringing
Below are examples of images with different ringing levels:
![Ring_Images](https://user-images.githubusercontent.com/43020938/156930957-3e30489a-0a1b-4a60-9708-9a95e7dd0209.png)

The following table contains the classification results after adding ringing effect to images:


### 4.6 Images with Ghosting
Below are examples of images with different ghosting levels:
![Ghost_Images](https://user-images.githubusercontent.com/43020938/156930978-dc6c93b2-bba3-476c-a383-bb874e333e18.png)

The following table contains the classification results after adding ghosting effect to images:
