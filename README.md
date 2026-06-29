# The PRAJNANA Dataset (Sample)
**Neural and Oculomotor Correlates of Moral Wisdom**

This repository contains a **5-subject public sample** of the **PRAJNANA** (pronounced: Pragyan) dataset. PRAJNANA is the first multimodal dataset ever conceived and specifically designed to study the nature of wisdom in decision making. The acronym stands for **P**erceptive, **R**eflective, **A**ffective, **J**udicious (good Judgement), **N**oble, **A**ltruistic, **N**ourishing, and **A**ware (self-awareness), capturing the essence of wisdom.

This synchronized, multimodal neurophysiological dataset of N = 30 Indian participants was designed to investigate the neural and physiological correlates of wisdom during moral conflict evaluation. 

## 🧠 Experimental Task & Paradigm
Participants were presented with 13 pictorial moral vignettes drawn from the **MWISE** (Multidimensional Wisdom Scale-Extended). The vignettes depict scenarios of varying moral complexity:
- **High Moral Conflict (HC):** e.g., witnessed violence, severe ethical dilemmas.
- **Low Moral Conflict (LC):** e.g., prosocial actions, ambiguous but non-threatening scenarios.

Participants engaged in a self-paced viewing paradigm where they evaluated the moral conflict presented on the screen. The task was programmed and presented using **Psychtoolbox-3**.

## 🔬 Hardware & Recording Specifications
The dataset features simultaneous, co-registered recordings of brain activity (EEG) and eye movements (ET):
- **EEG Acquisition:** Recorded continuously from 32 scalp electrodes using a **BrainProducts actiCHamp Plus** amplifier with active electrode technology. Data was recorded at 1,000 Hz (online reference: FCz) and subsequently downsampled to 500 Hz during preprocessing.
- **Eye-Tracking & Pupillometry:** Recorded simultaneously using a **Tobii Pro Fusion** eye-tracker operating at **120 Hz**, positioned below the stimulus display monitor.

## 📂 Repository Structure
This repository is a sample containing data for 5 participants (`G1P1` to `G1P5`):
- `EEG_Sample/`: Contains preprocessed, clean EEG epochs in MNE Python/EEGLAB `.fif` format.
- `EyeTracking_Sample/`: Contains processed eye-tracking data (Gaze X, Gaze Y, Pupil dilation) in `.mat` format, alongside corresponding trial event onset/offset timestamps (`_events.csv`).

## 🛠️ Data Preprocessing Pipeline
To prevent redundant effort and ensure reproducibility, please note that the data in this repository has already undergone the following preprocessing steps:

**EEG Preprocessing (in MNE-Python):**
1. **Filtering:** Notch-filtered at 50 Hz to suppress line noise.
2. **Downsampling:** Downsampled from 1,000 Hz to 500 Hz.
3. **Artifact Rejection:** Independent Component Analysis (FastICA with PCA variance threshold of 0.999) applied to remove ocular and muscular artifacts.
4. **Epoching:** Continuous data segmented into epochs from −200 ms to +5,000 ms relative to stimulus onset.
5. **Baseline Correction:** Corrected using the −200 ms to 0 ms pre-stimulus window.

**Eye-Tracking Preprocessing:**
1. **Missing Data:** Blinks and tracking losses were removed and linearly interpolated.
2. **Outlier Rejection:** Robust outlier detection applied using Median Absolute Deviation (MAD).
3. **Pupil Normalization:** Pupil diameter was baseline-corrected using the 0 to 500 ms post-stimulus window and z-scored to control for baseline luminance differences across scenes.
4. **Saccade Classification:** Fixations and saccades were parsed using the Velocity-Threshold Identification (I-VT) algorithm.

## 📥 Access to Full Dataset
The full PRAJNANA dataset consists of synchronized recordings for all N=30 subjects. To request access to the complete dataset for replication or secondary analysis, please contact the author.
