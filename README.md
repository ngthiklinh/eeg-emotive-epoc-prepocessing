EEG Signal Preprocessing & Visualization: MindBigData MNIST
This project provides a comprehensive pipeline for analyzing raw EEG signals from the Emotiv Epoc (EP) device. It focuses on converting raw, noisy brainwave data into standardized feature matrices suitable for machine learning classification

1. Project Goals

Pipeline Design: Implement a robust data ingestion and cleaning pipeline using Python (Pandas, NumPy, SciPy, and Matplotlib). 

Standardization: Resolve dimensional inconsistencies through resampling to ensure mathematical stability for neural classifiers. 

Signal Purity: Isolate pure neural activity by removing systemic DC offsets and attenuating physiological noise (muscle movements, eye blinks). 

Statistical Analysis: Generate uniform features using Z-Score normalization for 1D-CNN or other BCI (Brain-Computer Interface) decoders. 

2. Dataset Description
The project utilizes the MindBigData2022_MNIST_EP dataset. 

Device: Emotiv Epoc (14 channels: AF3, F7, F3, FC5, T7, P7, O1, O2, P8, T8, FC6, F4, F8, AF4). 

Stimulus: Captures cognitive responses to digits 0-9. 

Structure: Tab-separated raw signals without headers; each trial represents ~2 seconds of data at approximately 128Hz. 

3. Preprocessing Pipeline

Resampling: Signals are standardized to a fixed length of 256 samples using linear interpolation to ensure consistency across trials. 

DC Offset Removal: Subtracts the mean amplitude to center the signal at 0 µV, removing large systemic hardware biases (often >4000 µV). 
Filtering:

Bandpass Filter: 0.5 Hz to 40 Hz (Order 4) to remove slow drift and high-frequency muscle noise. 

Notch Filter: Targeted at 50 Hz to eliminate power line electrical hum. 

Normalization: Z-Score normalization to scale variance to 1, essential for deep learning convergence. 

4. Key Findings & Visualization
The analysis highlights the regional differences in brain activity:

Frontal Channels (F4, FC5): Captured the highest variability (STD ~137 µV), primarily due to artifacts like eye blinking and facial expressions. 

Occipital Channels (O2): Exhibited the lowest noise profiles, making them ideal for isolating Visual Evoked Potentials (VEP). 

Grand Average ERP: The smoothed peaks in the averaged waveforms (e.g., sample ~135) indicate consistent neural responses to digit stimuli. 

5. How to Use
Jupyter Notebook: Open emotive-epoc-preprocessing-notebook.ipynb to execute the code step-by-step.

