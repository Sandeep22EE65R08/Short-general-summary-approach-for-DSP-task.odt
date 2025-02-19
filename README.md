Digital Signal Processing (DSP) Approach

Jupyter Notebook

Step 1: Spectrogram Visualization of Real-Time Data

Generate a spectrogram to analyze time-varying frequency content.

X-axis: Time in seconds.

Y-axis: Frequency spectrum in Hz.

Color scale: Intensity (power) in dB.

Purpose: Identify frequency shifts, transient behavior, or patterns in time-varying signals.

Step 2: Spectral Analysis in the Frequency Domain

Power Spectral Density (PSD) Calculation & Plotting:

Apply a Hamming window to minimize spectral leakage.

Compute PSD using Welch’s method.

Perform frequency shifting to center the spectrum.

Compute mean PSD and display it.

Plot PSD with a log scale and highlight the mean PSD.

Frequency Spectrum Analysis:

Compute FFT to transform the signal into the frequency domain.

Shift the zero-frequency component to the center.

Create a frequency axis based on the sampling rate.

Plot the magnitude of the FFT for spectral analysis.

Step 3: Energy-Based Algorithm for Signal Packet Detection & Extraction

Apply a bandpass filter to isolate the desired frequency range.

Use a Butterworth filter with filtfilt for zero-phase distortion.

Compute energy as the squared magnitude of the filtered signal.

Apply a sliding window/moving average for smoothing.

Set an energy threshold based on noise level and scaling factor.

Identify start and end points of packets based on energy exceeding the threshold.

Plot energy profile and mark detected packets.

Extract packets using detected start/end indices.

Print start time, end time, and duration.

Step 4: Spectrogram Visualization of Extracted Packets

Generate spectrograms for all extracted packets to analyze frequency content.

Step 5: Frequency Offset Estimation for Signal Packets

Compute PSD using Welch’s method.

Identify frequency bands using a thresholding approach.

Estimate frequency offset from detected bands.

Step 6: Frequency Offset Correction for Signal Packets

Compute offset and correct it using: y(t) = y(t) × exp(j⋅2π⋅offset⋅t)

Verify correction using spectrogram visualization.

Step 7: Frequency Spectrum Analysis After Offset Correction

Compute FFT of the corrected packet.

Shift zero frequency to the center.

Plot the FFT magnitude for verification.

Step 8: Power Spectral Density (PSD) Analysis After Offset Correction

Apply Hamming window.

Compute PSD using Welch’s method.

Normalize and plot PSD with log scale.

Step 9: Low-Pass Filtering or DFT Low-Pass Filter After Frequency Offset Correction

Filtering using Low-Pass Filter:

Design a Butterworth low-pass filter with a cutoff frequency.

Apply zero-phase filtering (sosfiltfilt).

Plot spectrogram after filtering.

Filtering a Signal Using the DFT:

Compute the DFT of the input signal using np.fft.fft.

Multiply the DFT of the input signal with the frequency response of the desired filter.

Compute the inverse DFT of the resulting product using np.fft.ifft to obtain the filtered signal.

Step 10: Frequency Spectrum Analysis After Filtering

Compute FFT after filtering.

Analyze spectral content and plot FFT magnitude.

Step 11: PSD Calculation After Filtering

Compute PSD using Welch’s method.

Apply a Hamming window if needed.

Shift and normalize PSD.

Plot PSD with mean level.

Step 12: SNR Calculation After Filtering of Signal Packets

Compute signal power by integrating the PSD within the specified signal frequency band.

Compute noise power by integrating the PSD within the specified negative and positive noise frequency bands.

Compute the Signal-to-Noise Ratio (SNR) in decibels (dB) using the formula:
SNRdB = 10 * log10(Psignal / Pnoise)

Interpret SNR to evaluate signal quality after filtering.

Step 13: Skewness and Kurtosis Calculation with KDE Plot for Filtered Signal Magnitude

Compute skewness:
Skewness = (n / ((n - 1) * (n - 2))) * Σ((|x_i - μ|) / σ)^3

Compute kurtosis:
Kurtosis = (1 / n) * Σ((|x_i - μ|) / σ)^4 - 3

Classify skewness and kurtosis (symmetric, leptokurtic, platykurtic).

Estimate Probability Density Function (PDF) using Kernel Density Estimation (KDE).

Step 14: Pattern Detection and Extraction

Compute energy of each sample: Energy = |x_i|^2

Apply a moving average to smooth energy.

Set an energy threshold to identify patterns.

Detect and extract patterns based on duration.

Visualize energy profile and detected patterns.

Step 15: Skewness and Kurtosis Computation for Extracted Patterns

Compute skewness and kurtosis for each pattern.

Classify results (symmetric, skewed, sharp/flat peak).

Generate KDE plot for each pattern to visualize amplitude distribution.

Tools & Technologies Used

Programming: Python (NumPy, SciPy, Matplotlib)

Signal Processing Techniques: FFT, Welch’s Method, Bandpass & Low-Pass Filtering, Frequency Offset Estimation

Visualization Tools: Inspectrum, Spectrograms, KDE Plots

Project Outcome

Achieved successful detection, extraction, and analysis of signal packets with improved SNR. The integrated DSP techniques provided enhanced signal characterization and pattern recognition.

