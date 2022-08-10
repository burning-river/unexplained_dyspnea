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



