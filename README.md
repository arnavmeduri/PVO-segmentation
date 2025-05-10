# Using Deep Learning to Screen for Retinal Tears in Patients with Acute, Symptomatic Posterior Vitreous Detachments

### Overview

Retinal tears (RTs) are full-thickness breaks in the neurosensory retina that occur most commonly after posterior vitreous detachments (PVDs). These tears can allow fluid to enter the subretinal space and lead to retinal detachment if not promptly treated.

This project focuses on developing deep learning models to identify posterior vitreous opacities (PVOs) in spectral domain optical coherence tomography (SD-OCT) scans as a method for screening RTs in patients with acute, symptomatic PVDs. A total of 500 SD-OCT scans were collected retrospectively from 100 eyes of 93 patients who presented with symptoms of flashes and/or floaters for less than 32 days. Each scan was reviewed and annotated by trained graders to identify PVOs, which were used as ground truth for model training.

### Methods

Two deep learning models were developed for automated PVO detection: a 2D U-Net model and a FRCNN (Faster Region-Based Convolutional Neural Network). Both models were implemented in PyTorch and evaluated using five-fold cross-validation at the subject level. The U-Net architecture was modified with ResNet blocks and trained with a loss function combining Dice loss and binary cross-entropy. The FRCNN model was trained separately using standard region proposal components. To generate PVO counts from segmentation outputs, the determinant of the Hessian matrix was applied as a postprocessing step. The models were assessed by comparing automated PVO counts to ground-truth annotations and using these counts to predict the presence of a retinal tear. A threshold of 15 or more PVOs on at least one raster scan was used as the indicator for retinal tear classification.

<table>
  <tr>
    <td align="center">
      <img width="336" alt="image" src="https://github.com/user-attachments/assets/02c69212-ded9-4b27-a876-f10fb9b4c19b" />
    </td>
    <td align="center">
      <img width="336" alt="image" src="https://github.com/user-attachments/assets/634c5573-e204-4958-8dbe-a6c06f7f12b7" />
    </td>
  </tr>
</table>

### Results

The U-Net model achieved a mean difference of -0.472 ± 3.03 PVOs from the ground truth and an F1-score of 1 when predicting RTs. U-Net outperformed FRCNN across nearly all validation folds in count accuracy and segmentation quality. Dice scores reached up to 0.934 (average 0.651 ± 0.145), indicating strong agreement between prediction and manual annotation. This project demonstrates that automated detection of PVOs in SD-OCT imaging can be a reliable method for RT screening in patients with acute, symptomatic PVDs. Additionally, the models and methods described here provide a foundation for future clinical tools that support more timely and accurate retinal tear diagnosis using artificial intelligence.
