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



The first principal component explains 7% of the variance. The theta of the first principal component was obtained by calculating the mean theta. 

See below the **plot of theta for each frequency** for the first session of the first mouse.
Colors for each frequency:
For 2,000 Hz: red.
For 4,000 Hz: yellow.
For 8,000 Hz: magenta.
For 16,000 Hz: green.
For 32,000 Hz: blue.


