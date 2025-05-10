# Using Deep Learning to Screen for Retinal Tears in Patients with Acute, Symptomatic Posterior Vitreous Detachments

### Overview

This project focuses on developing deep learning models to identify posterior vitreous opacities in Spectral Domain Optical Coherence Tomography (SD-OCT) scans as a method for screening retinal tears in patients with acute, symptomatic posterior vitreous detachment. A total of 500 SD-OCT scans were collected retrospectively from 100 eyes of 93 patients who presented with symptoms of flashes and/or floaters for less than 32 days. Each scan was reviewed and annotated by trained graders to identify posterior vitreous opacities, which were used as ground truth for model training. Patients with a history of retinal tear, vitrectomy, uveitis, diabetic retinopathy, or retinal vein occlusion were excluded.

### Retinal Tear Background

Retinal tears are full-thickness breaks in the neurosensory retina that occur most commonly after posterior vitreous detachment. These tears can allow fluid to enter the subretinal space and lead to retinal detachment if not promptly treated. Early detection is critical for preventing vision loss. Two deep learning models were developed for automated posterior vitreous opacity detection: a 2D U-Net model and a FRCNN (Faster Region-Based Convolutional Neural Network). Both models were implemented in PyTorch and evaluated using five-fold cross-validation at the subject level. The U-Net architecture was modified with ResNet blocks and trained with a loss function combining Dice loss and binary cross-entropy. The FRCNN model was trained separately using standard region proposal components. To generate posterior vitreous opacity counts from segmentation outputs, the determinant of the Hessian matrix was applied as a postprocessing step. The models were assessed by comparing automated posterior vitreous opacity counts to ground-truth annotations and using these counts to predict the presence of a retinal tear. A threshold of 15 or more posterior vitreous opacities on at least one raster scan was used as the indicator for retinal tear classification.

### Methods and Results

The U-Net model achieved a mean difference of -0.472 ± 3.03 posterior vitreous opacities from the ground truth and an F1-score of 1 when predicting retinal tears. U-Net outperformed FRCNN across nearly all validation folds in count accuracy and segmentation quality. Dice scores reached up to 0.934 (average 0.651 ± 0.145), indicating strong agreement between prediction and manual annotation. This project demonstrates that automated detection of posterior vitreous opacities in SD-OCT imaging can be a reliable method for retinal tear screening in patients with acute, symptomatic posterior vitreous detachment. The models and methods described here provide a foundation for future clinical tools that support more timely and accurate retinal tear diagnosis using artificial intelligence.




