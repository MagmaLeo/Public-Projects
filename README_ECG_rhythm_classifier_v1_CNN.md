Files:

  ECG_rhythm_classifier_v1_CNN.ipynb -> main notebook
  
  ptbxl_rhythms_CNNmodel.keras -> final model
  
  ptbxl_rhythms_CNNmodel.h5 -> same final model, but h5 format
  
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ 

Description:

Utilized a (ECG) dataset from PTB_XL (see: https://physionet.org/content/ptb-xl/1.0.1/#files-panel) and personal CNN architecture to train on 12-lead ECG signals with assigned rhythm labels (in order to create a multi-label prediction model for rhythms of an ECG).

Procedure:
1. Data read in and processed
2. Data split into train/val/test sets
3. CV
4. Training
5. Run on test set (+ model saved as "ptbxl_rhythms_CNNmodel" file)
6. Provided numerical results for F1-Score, Sensitivity, Specificity, Precision, Accuracy 
7. Displayed bar graphs for each of these metrics (bars on x-axis categorized by class, with class labels' bars ordered from those with highest to lowest F1-score, height based on true number of signals that were assigned a given class's label, and color based on the main metric for the plot);  The reason for the inclusion of true number of signals is to keep in mind the class imbalance and observe expected trends whereby classes with worse metrics where ones with fewer examples.
8. Provided a heat map containing all of these metrics for all class labels
9. Displayed a few examples from the test set of 12 lead ECG's and their true vs predicted labels

Note: Certain steps, architecture, and parameters were used, so the results shown are dependent on what I last used. Examples of specific parameters include using 5sec worth of samples for each 500Hz signal, or setting threshold to 0.5 for class label probabilities of labels to be considered "positive" for the class (and using my "option 1" method such that if any fall below 0.5, then no label is given -> "option 2" still allows for 1 (or more) label to be assigned if p>=0.5, but has the fallback of assigning the highest probability class for a given signal if no labels for a given signal had p>=0.5).

As for the possible v2 model, I have begun setting up a Bidirectional LSTM with Attention architecture, and with data augmentation to better adjust for serious class imbalance.
