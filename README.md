
# 🧠 Brain-to-Brain Decoding using CEBRA


## Overview

This project aims to decode the temporal dynamics arising from the coordination of multiple neural systems during social     interaction. Using hyperscanning EEG data, we analyze joint neural activity and behavioral signals to learn structured representations through the CEBRA framework.



⚙️ What this project does

               The notebook implements a full pipeline:

                                        EEG preprocessing (ICA, bad channel handling)
                                        Temporal alignment of dyadic signals
                                        Neural embedding using CEBRA
                                        Behavioral decoding using KNN


Evaluation using:

    KNN decoding score
    Goodness-of-Fit (R²)
    Shuffle control

    
📊 Results
  KNN (Main Model): ~0.99
  Shuffle Control: ~ (-0.98)
  GOF (Train): ~0.77
  GOF (Test): ~0.76
  👉 The model learns structured embeddings for behavioral states, while shuffled controls produce non-meaningful representations.


  

📁 Repository Structure
.
├── cleaned_edf/                     # Preprocessed EEG data (artifact removed)
├── brain_to_brain_decoder.ipynb     # Main notebook (full pipeline)
└── README.md




🔍 Key Observations
      Clear clustering of behavioral states in embedding space
      Minor overlap indicates transitional neural activity or noise
      Shuffle control destroys structure → confirms meaningful learning
      High performance on single dyad suggests possible dyad-specific learning

    
⚠️ Limitation

    This analysis is performed on a single dyad, which limits generalization.
    The model may learn subject-specific patterns rather than universal neural representations.

--------

This project is currently under development and includes my ML4Sci Neurodyads evaluation task implementation.

