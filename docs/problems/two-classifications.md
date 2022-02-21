---
layout: default
title: Classification of 2 Classes (With or Without Tumor)
parent: Problems
nav_order: 1
---

# Classification of 2 Classes (With or Without Tumor)
{: .no_toc }

Topic text
1. INTRODUCTION

The process of diagnosing brain tumors from magnetic resonance imaging (MRI) is often time-consuming. Thus, a rapid analyses through an automated system could help improve the treatment possibilities and optimize hospital resources. The following neural network classifies MRI images as tumoral and non-tumoral.

2. MATERIALS AND METHODS
2.1 BRATS2020 Dataset

We conducted our experiments using the data available in the Multimodal Brain Tumor Segmentation Challenge 2020 (BRATS2020) dataset [17]. The BRATS2020 dataset has images of MRI scans and describe a) native (T1), b) post-contrast T1-weighted (T1Gd), c) T2-weighted (T2), and d) T2 Fluid Attenuated Inversion Recovery (T2-FLAIR) volumes. The images were acquired from 371 patients, using diff erent clinical protocols and various scanners from 19 institutions. For each patient, there are four MRI 3D scans. The images have been manually segmented, by one to four raters, following the same annotation protocol. Annotations comprise the GD-enhancing tumor (ET — label 4), the peritumoral edema (ED — label 2), and the necrotic and non-enhancing tumor core (NCR/NET — label 1). In the present study, 8,099 axial 2D MRI slices were extracted from the 3D MRI flair images. The slices were randomly extracted and the masks were used only to indicate the presence of a brain tumor in each slice. Among the 8,099 2D MRI scans, 3,999 scans (49.4%) contain tumors and 50.6% do not, providing a balanced dataset.

3. CNN BRAIN TUMOR DETECTION MODEL

To identify if an image has a tumor, we used a CNN-based classification system. More specifically, we considered the Resnet18 architecture. While training the architecture, we used the cross-entropy as the loss function and Adam as the optimizer. We considered batches of 64 sub-images with a default learning rate of 0.002. All evaluated architectures were pre-trained, using weights imported from the Imagenet dataset. The last layer of the network was trained using the BRATS2020 dataset (for a dataset description, see Section 2.1. To perform this training, we used 80% of the images for training and 20% of the images used for test. As mentioned earlier, each of these subsets contains approximately 50% of the images with tumors and the remaining 50% of the images without tumors. The patients from the training set were different from those in test set. To avoid any bias in the dataset split, a 𝑘 -fold was used with 𝑘 = 10. The results are presented in the next section.

