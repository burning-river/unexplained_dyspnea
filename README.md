# File Description

1. prediction\_clinical.ipynb: Contains PkVO2 prediction from clinical features.

2. prediction\_combined.ipynb: Contains PkVO2 prediction by combining clinical, shape and texture features.

3. shape\_analysis.ipynb: Contains outlier analysis, U test and regression analysis of shape features.

4. shape\_feature\_extraction.ipynb: contains code for volume, pyradiomics and 3D fractal feature extraction.

5. texture\_3d\_feature\_extraction.ipynb: contains code for outlier analysis, U test and regression analysis of texture features. 

# RESEARCH SUMMARY

## PURPOSE: 
Unexplained dyspnea is common in patients with chronic HIV infection and may represent a consequence of subclinical cardiac and pulmonary dysfunction. Performance of cardiopulmonary exercise testing (CPET) in concert with cardiac magnetic resonance imaging may provide direct imaging correlates of cardiopulmonary dysfunction reflected through parameters such as peak oxygen consumption (PkVO2). We posit that myocardial shape and texture features from cardiac cine magnetic resonance imaging (CMR) may correlate with PkVO2 reflecting latent subclinical cardiac dysfunction.

## MATERIALS AND METHODS: 
Prospective cohort study of HIV positive subjects is done with subjective Grade 2 or 3 dyspnea on the Medical Research Council (MRC) scale without evidence of gross cardiac or pulmonary abnormalities by echo, chest x-ray and/or CT. Short-axis cine CMR scans are obtained in a 1.5T MRI simultaneously with CPET on a MRI compatible treadmill attached to the scanner. The left ventricle (LV) and myocardium are segmented using a pretrained UNet model that are improved upon by manual segmentation by an expert cardiologist. This is followed by extraction of 2D and 3D shape and texture features during a cardiac cycle including the end-systole (ES) and end-diastole (ED). Clinical features are combined with those extracted from radiomics to predict PkVO2.

## PREVIOUS WORK AND INNOVATION: 
Our group has done a substantial amount of work in CT radiomics for characterization of prognosis and prediction of therapeutic response based on sophisticated shape-based features from cardiac chambers. In this study, we seek to extract shape features from rest and stress MRI to provide an accurate cardiac based etiology for unexplained dyspnea using MR-CPET augmented approach. This would aid in refined understanding of the pathophysiology of the underlying cardiac mechanism of dyspnea and identify patients at risk for heart failure or other adverse event as a resultant of prolonged dyspnea.

## APPROACH: 
• Aim 1 (Segmentation): We use the nnUNet model to automatically segment cardiac chambers from rest and stress cine MRI from short axis, 2 chamber views. We further fine-tune the segmentations manually supervised by an expert cardiologist.

• Aim 2 (Shape and texture Analysis): Extract and evaluate shape and texture features from the segmented chambers.

• Aim 3 (PkVO2 prediction): Retrospectively predict and provide a cardiac etiology for dyspnea (using CPET derived PkVO2 as a surrogate) employing shape and texture features from rest MRI. 

## RESULTS:
1. The left ventricle (LV) and myocardium were segmented using a pretrained UNet model that were improved upon by manual segmentation by an expert cardiologist. 
2. This was followed by extraction of 2D and 3D shape and texture features during a cardiac cycle including the end-systole (ES) and end-diastole (ED). The shape features included Euclidean distance between pixels, surface area and volume of the ROI. The texture features included 3D Laws - where a filter of size 3x3x3 detecting edges (E3), levels (L3) and spots (S3) is convolved with the image to estimate texture energy - and 3D Gabor - where a filter with size modulated by a Gaussian function detects frequency (represented by 2π/λ) contents in images as well as their orientations (θ) along the XY and XZ planes. We posited that demographic, myocardial shape and texture features from cine CMR may correlate with PkVO2 reflecting latent subclinical cardiac dysfunction. 
3. We extracted a total of 191 2D & 3D shape features and 824 3D-texture features (median, variance, kurtosis and skewness of 103 features for both LV and myocardium at ED and ES phases). A multivariate linear regression model was able to modestly predict PkVO2 - coefficient of determination R2 = 0.56 <ins>+</ins> 0.02 for 100 bootstrapped validation sets. The six features used by the model were: 
• height, 
• kurtosis-Laws E3E3L3, • LV-ED (anticorrelation), 
• median-Laws E3E3S3 for LV at ED (anticorrelation), 
• kurtosis-Gabor XY-θ=0.785, XZ-θ=0.785, λ=0.880, LVMC-ES, • median LV surface-volume ratio (anticorrelation) and 
• kurtosis-Gabor XY-θ=2.356, XZ-θ=0.785, λ=0.880 for LV at ED. 
We used the average values of the coefficients from the 100 iterations and predicted the PkVO2 with an R2 of 0.72. 
