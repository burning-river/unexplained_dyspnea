# File Description

• shape\_feature\_extraction.ipynb: contains code for volume, pyradiomics and 3D fractal feature extraction.

• shape.ipynb: contains code for univariate and multi-variate regression analysis to find association between PkVO2 (max oxygen intake during exercise) and PetCO2 (Partial pressure of exhaled CO2, can be a measure of of pulmonary blood flow) and shape features.

• prediction.ipynb: contains code for building a classifier to predict high and low PkVO2 patients. 

# RESEARCH SUMMARY

## PURPOSE: 
Unexplained dyspnea is common in patients with chronic HIV infection and may represent a consequence of subclinical cardiac and pulmonary dysfunction. Performance of cardiopulmonary exercise testing (CPET) in concert with cardiac magnetic resonance imaging may provide direct imaging correlates of cardiopulmonary dysfunction reflected through parameters such as peak oxygen consumption (PkVO2). We posit that myocardial shape and texture features from cardiac cine magnetic resonance imaging (CMR) may correlate with PkVO2 reflecting latent subclinical cardiac dysfunction.

## MATERIALS AND METHODS: 
Prospective cohort study of HIV positive subjects is done with subjective Grade 2 or 3 dyspnea on the Medical Research Council (MRC) scale without evidence of gross cardiac or pulmonary abnormalities by echo, chest x-ray and/or CT. Short-axis cine CMR scans are obtained in a 1.5T MRI simultaneously with CPET on a MRI compatible treadmill attached to the scanner. The left ventricle and myocardium is segmented using a pretrained UNet model followed by extraction of 2D and 3D shape features. Patients are dichotomized into those above and below 80% of the predicted PkVO2 value. We explore features that differentiate the two groups and will perform uni/multivariate analyses and machine learning techniques using shape features to predict PkVO2.

## PREVIOUS WORK AND INNOVATION: 
Our group has done a substantial amount of work in CT radiomics for characterization of prognosis and prediction of therapeutic response based on sophisticated shape-based features from cardiac chambers. In this study, we seek to extract shape features from rest and stress MRI to provide an accurate cardiac based etiology for unexplained dyspnea using MR-CPET augmented approach. This would aid in refined understanding of the pathophysiology of the underlying cardiac mechanism of dyspnea and identify patients at risk for heart failure or other adverse event as a resultant of prolonged dyspnea.

## APPROACH: 
• Aim 1 (Segmentation): We use the nnUNet model to automatically segment cardiac chambers from rest and stress cine MRI from short axis, 2 chamber views. We aim to extract volumetric features from the cardiac components.

• Aim 2 (Shape and texture Analysis): Extract and evaluate shape and texture features from the segmented chambers.

• Aim 3 (Dyspnea prediction): Retrospectively predict and provide a cardiac etiology for dyspnea (using CPET derived PkVO2 as a surrogate) employing 
a. shape and texture features from rest MRI 
b. combination of features from rest and stress MRI, integrating baseline patient characteristics, echo and EKG measurements.

## RESULTS:
The left ventricle (LV) and myocardium were segmented using a pretrained UNet model followed by extraction of 2D and 3D shape features. Patients were dichotomized into those above (_n_ = 19) and below 80% (_n_ = 32) of the predicted PkVO2 value. We posited that myocardial shape and texture features from cine CMR may correlate with PkVO2 reflecting latent subclinical cardiac dysfunction. We explored features that differentiate the two groups using the Mann Whitney U-test and performed regression analyses using shape features to predict PkVO2. 

• The standard deviation of the LV volume (_p_ = 0.049), LV sphericity (_p_ = 0.02) and LV maximum surface area (_p_ = 0.04) during a cardiac cycle were the most significant features in distinguishing subjects with high and low PkVO2. 

• A model incorporating X and Y was able to modestly predict PkVO2 (_R2_ = 0.38), with the minimum myocardium volume (_p_ = 0.002) and median LV surface to volume ratio (_p_ = 0.006) during a cardiac cycle being the most significant features. 

• A multi-regression model predicted PetCO2 with an _R2_ of 0.5 where the maximum LV diameter in the sagittal plane (_p_ < 0.0005) and median LV surface to volume ratio (_p_ = 0.006) were the most important features.

• We report a ROC AUC of 0.65 <ins>+</ins> 0.06 using a random forest classifier on 100 iterations of cross-validation. 
