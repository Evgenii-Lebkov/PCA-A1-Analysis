# Principal Component Analysis of Neuronal Response in the Mouse Primary Auditory Cortex to Single Tone Stimuli

## Hypothesis:

The range of the human ear is 20 to 20,000 Hz. Mice can hear sounds with frequencies above 80,000 Hz (Turner et al, 2005, P. 4). Since mice are tuned to higher frequency ranges, it is possible that they might hear lower frequencies worse. Probably, the neuronal response in the primary auditory cortex to lower frequencies will be less intense than to higher frequencies.

## To test this hypothesis, the following dataset was used:

**Dataset source**: https://dandiarchive.org/dandiset/000986/0.251031.1939

**Dataset name**: Auditory cortex Neuropixels recordings and pupil diameter traces from mice during passive exposure to pure tones

**Dataset created**: October 31, 2025

**Dataset description by authors**: In these experiments, neural activity was recorded from auditory cortex of behaving mice during passive tone presentation and arousal state was simultaneously monitored using pupillometry. This dataset contains: (1) spike times of sorted units obtained from **Neuropixels 1.0** recordings of auditory cortex of head-fixed mice; in each session, neural recordings were made during periods of silence (spontaneous activity) and during passive presentation of **brief pure tones** (**2-32 kHz**, evoked activity); (2) pre-processed and max-normalized pupil diameter traces for each recording session; (3) pre-processed running speed traces for each recording session. The dataset includes **15 sessions** from **5 different mice**. For more information on the data acquisition and processing, please see the preprint associated with this dataset: **https://doi.org/10.1101/2024.04.04.588209**.

Papadopoulos, L., Jo, S., Zumwalt, K., Wehr, M., Jaramillo, S., McCormick, D. A., Mazzucato, L., National Institutes of Health, National Institutes of Health, National Institutes of Health, National Institutes of Health, National Institutes of Health, & National Science Foundation. Auditory cortex Neuropixels recordings and pupil diameter traces from mice during passive exposure to pure tones (Version 0.251031.1939) [Data set]. DANDI Archive. https://doi.org/10.48324/dandi.000986/0.251031.1939

## Extracted data was analyzed using the following methods:

**Principal Component Analysis**. Data was collected from more than 200 neurons. Analyzing the activity of each neuron individually is computationally expensive. Therefore, spike data was represented in a new basis to perform dimensionality reduction using the PCA method. The first inferred principal component, which explains approximately 7% of the variance, was analyzed.

**Linear Gaussian Model**. The computational model can be characterized as a “What” model that performs encoding, as it mathematically describes the neuronal response to stimuli. After performing PCA, the activity of these components is described as a non-discrete value, and the noise can be viewed as Gaussian. The goal is to find the hidden parameter theta.

**Equation:**

$y = \theta \cdot x + \eta$

where $x$ is the stimulus, $\theta$ is the window of the pattern of neuronal activity caused by the stimulus, and $\eta$ is Gaussian noise.

Denoising was performed by finding the mean theta for each particular type of stimulus in every session.

## Analysis procedure:

There were 5 mice, with several sessions for each mouse. It was decided to analyze only specific time windows that contain the stimulus plus fixed intervals before and after it. The time window starts 0.1s before the stimulus onset and ends 0.3s after it. With a delta t of 0.01s, each time window consists of 40 bins. The activity of every neuron was distributed into these bins.

Five matrices were created, one for each of the five sound frequencies, and each frequency was analyzed independently. As a result, time windows for the activity of more than 200 neurons were obtained, and dimensionality reduction by PCA was performed afterwards.

The eigenvectors and eigenvalues of the covariance matrix were calculated, and the data was transformed into a new basis. The first principal component was chosen to find theta.

**Variance explained by components:**

<img width="557" height="413" alt="Image" src="https://github.com/user-attachments/assets/988ac79e-8c30-41b6-bc9b-96f815acbb6c" />

The first principal component explains 7% of the variance. The theta of the first principal component was obtained by calculating the mean theta. 

See below the **plot of theta for each frequency** for the first session of the first mouse.

Colors for each frequency:
For 2,000 Hz: red.
For 4,000 Hz: yellow.
For 8,000 Hz: magenta.
For 16,000 Hz: green.
For 32,000 Hz: blue.

<img width="709" height="528" alt="Image" src="https://github.com/user-attachments/assets/6cf82157-fa70-4dc6-a300-5b8e1391426c" />

Plots for every session of every mouse were found using the same methods. The mean theta for every mouse was found as well. See below the **mean theta for all sessions of the first mouse**:

<img width="718" height="527" alt="Image" src="https://github.com/user-attachments/assets/d922739b-b0c8-4c4b-8ee3-c3f9be848981" />

**The overall mean thetas for every mouse across all their sessions were found:**

<img width="668" height="501" alt="Image" src="https://github.com/user-attachments/assets/e3fc4e18-366c-43e5-b147-58e3992ce129" />

Peak values for thetas:

Peak values (2k, 4k, 8k, 16k, 32k): 0.2453350269895592, 0.17388835025236776, 0.30676480744535983, 0.3465176134484306, 0.24339926839819753

Peak times: 0.02, 0.02, 0.02, 0.02, 0.02

The peak for 4,000 Hz is the lowest, and the peak for 16,000 Hz is the highest. The second highest peak is at 8,000 Hz. The peaks for 2,000 Hz and 32,000 Hz are in the middle and are nearly identical.

Analysis of these plots shows that there is no linear dependence between the neuronal response and sound frequency.

See below the obtained plot showing the **dependence of the neuronal response on sound frequency**:

<img width="616" height="446" alt="Image" src="https://github.com/user-attachments/assets/c7d49a43-ed88-471d-8c6a-38cbdb9c4697" />

See below the data on the **hearing ranges of different animals including mice**.

<img width="743" height="469" alt="Image" src="https://github.com/user-attachments/assets/839a6127-4229-42af-8713-dd0f490eb611" />

*Source: Turner et al., 2005, P. 23.*

The hearing range data is consistent with the acquired results. 2 and 4 kHz are heard by mice nearly equally poorly compared to other sounds in the 2–32 kHz range. According to the plot, 8 kHz is heard better than 2 and 4 kHz, and 16 kHz is heard even better than 8 kHz. In turn, 32 kHz is heard worse than 16 kHz, but better than 2 and 4 kHz.

## Conclusion

The performed analysis demonstrates that the dependence between the sound frequency and the neuronal response is not linear but parabolic. These results are consistent with scientific data that supports the non-linearity of this dependence.

## References

Turner JG, Parrish JL, Hughes LF, Toth LA, Caspary DM. Hearing in laboratory animals: strain differences and nonauditory effects of noise. Comp Med. 2005 Feb;55(1):12-23. PMID: 15766204; PMCID: PMC3725606.
