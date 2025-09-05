# README

This data set is described in Sherefati et al. “A high-density diffuse optical tomography dataset of naturalistic viewing”. 

Traditional laboratory tasks offer tight experimental control, but lack the richness of our everyday human experience. As a result many cognitive neuroscientists have been motivated to adopt experimental paradigms that are more natural, such as stories and movies. Here we describe data from 58 healthy adult participants (aged 18-76 years) who viewed at least 10 minutes of a movie (The Good, the Bad, and the Ugly, 1966); 36 of the participants viewed the clip more than once, resulting in 106 sessions of data. The data were collected on a custom high-density diffuse optical tomography system (~1200 total measurements), covering large portions of the superficial aspects of occipital, temporal, parietal, and frontal lobes. Data are provided in both channel format and projected to standard space, using an atlas-based light model. The data are suitable for methods exploration as well as a wide variety of cognitive phenomena.


## Stimuli and paradigm
Participants watched a 10-minute clip from The Good, the Bad, and the Ugly (1966). Some participants returned for multiple sessions and watched the same clip again, facilitating test-retest reliability or validation analyses.

## Preprocessing
Data pre-processing was done using the NeuroDOT toolbox based on the principles of modeling light emission, diffusion, and detection through the head. The latest version of the NeuroDOT toolbox can be found at https://www.nitrc.org/projects/neurodot. These preprocessed data were then converted to .nii file format for analysis and sharing purposes. Additionally, the `ndot2snirf` function in NeuroDOT was used to convert the raw data to SNIRF file format followed by `snirf2bids` function to generate other necessary metadata files to satisfy the BIDS specification for NIRS.


## Neuroimaging file types and organization
Data are provided in three formats: NeuroDOT (.mat file), SNIRF (.snirf file), and NIfTI (.nii file).

The NIfTI files follow standard BIDS naming conventions for fMRI data, with the NeuroDOT and SNIRF files living in a folder named `nirs` fore each participant.


## Validity of SNIRF files

Note that if you are using the Pysnirf2 Validator on this dataset, "fatal" errors will appear. These "Fatal" errors indicate an incompatibility with the Pysnirf2 Validator itself, but does not actually indicate the files are invalid. The Matlab toolbox  jsnirfy (https://github.com/NeuroJSON/jsnirfy) was used to create the SNIRF files for this dataset, which saves string-like variables as HDF5 datasets which are not accepted by the Pysnirf2 Validator. Despite these "Fatal" errors, Pysnirf2 is still able to successfully load the SNIRF files as expected.


## Important note on timing information

For the SNIRF and NeuroDOT formatted data, the onset of the movie varies across participants. For each subject, the onset time is provided in the SNIRF file.

For the NIfTI formatted data, extraneous data points have been trimmed. Thus time 0 of the data (i.e., the first frame) coincides with the onset of the movie. 
