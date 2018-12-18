
PROJECET TITLE:  UT-Fibers

Construct an algorithm to guess different textiles based on their IR spectra 


INTRODUCTION

Identification of textile fibers is important in industry (quality control), forensic science (identification of fibers on crime scene), but also in conservation and archaeology (identification of historical textile fibers). Common methods for fiber identification are microscopic observation, burning test and various solubility tests. Infrared spectroscopy (IR) has many advantages for fiber identification, because it offers highly characteristic information, is easy, fast, non-destructive and relatively inexpensive. However the analysis of IR spectra is tedious and requires a trained scientist and some peak-analyzer software. The main difficulties are spectral inhomogeneities of repeated measurements and the intrinsic similarity between the spectra of some fibers. Hence, a better method to analyze the IR specta of textiles is needed.


OBJECTIVES

To meet the increasing demand from the academic and industry, we aimed build a classifier that can identify fibers by their IR spectra. The initial aim is to be able to detect pure fibers at 80% probability.

For successful classification, we aimed to:
• reduce the complexity of the dataset
• engineer additional features from the dataset
• generate data normalization tools


PREREQUISITES FOR RUNNING THE CODE

* Raw file (from e.g. Thermo Scientific Nicolet 6700 FT-IR spectrometer with a  “Smart Orbit” micro-ATR accessory) that contains the ATR-FT-IR spectra of textile fibre(s). The output of the file is a simple array of 1700+ comma-separated value-pairs: wave-number with excitation values (5.997784e+002;1.240308e+000, 6.017070e+002;1.231942e+000, 6.036356e+002;1.226984e+000,...).
* Jupyter Notebook with all listed libraries installed.


INCLUDED FILES

'Balancing.ipynb' 
Load a dataset with 438 IR spectra of 12 different fiber types (labels). Balance the dataset by oversampling to get 30 instances of each label. Use this for training_data and the rest for testing_data

'Feature_exploration_v2_181214.ipynb'
File containing feature engineering functions for rows (IR-spectra):
- Function to calculate difference from global mean
- Function to calculate difference from local average (with sliding window)
- Function to calculate angles for line (with sliding window)
- Function to fill in NAN values in the Spectra using linear interpolation (as some datafiles have NANs in data)
- Function to standardize df row values (subtract the mean value and divide with std, giving distance from mean in std units)
- Function to normilize df row values (rescale to 0...1 from min and max values)
Plots to visualize the spectra and to analyze the correlation of new features on the same data (analyzing new feature usefulness).

'RF_kNN_SVM_all_features_181217_v2.ipynb'
Learning and testing different models on data from 'Balancing.ipynb' and prepared with features from 'Feature_exploration_v2_181214.ipynb'.

'rf.pkl'
Saved best model (with pickle dump)

'Classifier for users.ipynb'
Case study where feature-engineering and a trained model on test_data is used to predict the type of 4 unique fibers based on their IR-spectra, using the trained model from above.

'Poster_UT-fibers.pfd'
Poster of the project
