
# HRV

This is a Python module for performing heart rate variability (HRV) analysis on electrocardiogram (ECG) time series. 

## Prerequisites
* [NumPy] (http://www.numpy.org/)
* [Matplotlib] (http://matplotlib.org/)
* [SciPy] (https://www.scipy.org/)

## R-Peak Detection
### Pan-Tompkins

Implements the popular QRS complex detection algorithm introduced in:

[Pan, Jiapu, and Willis J. Tompkins. "A real-time QRS detection algorithm." *IEEE transactions on biomedical engineering* 3 (1985): 230-236.](https://www.researchgate.net/profile/Keesam_Jeong/publication/3728672_A_simple_real-time_QRS_detection_algorithm/links/54e829e10cf2f7aa4d4f64a9.pdf)

The algorithm uses filtering, adaptive thresholding, and criteria based on human cardiac physiology to detect QRS complexes in the face of noise and quickly changing and diverse ECG morphologies. This function implements the Pan-Tompkins algorithm as it was originally published, along with two modifications which include additional filtering and eliminating potential QRS detections that occur
within the refractory period.Since this algorithm is often used to find R-peak locations (and not just general QRS detection) for applications such as Heart Rate Variability (HRV) analysis, this function also performs a neighborhood search
around the final QRS detection locations to find exact R-peak locations.

<img src="https://github.com/pickus91/HRV/blob/master/figures/Original%20Signal.png" align="center" height="400" width="500">
<img src="https://github.com/pickus91/HRV/blob/master/figures/Final%20R%20Peak%20detection_Init%20Phase.PNG" align="center" height="400" width="480">

## HRV Features
### Time Domain 



### Frequency Domain 

### Poincare 

### Multifractal Detrended Fluctuation Analysis (MF-DFA)
Multi-fractal detrended fluctuation analysis (MF-DFA) introduced in:

Kantelhardt, Jan W., et al. "Multifractal detrended fluctuation analysis of 
nonstationary time series." *Physica A: Statistical Mechanics and its Applications*
316.1 (2002): 87-114

MF-DFA is based on the standard detrended fluctuation analysis (DFA) introduced by [Peng, *et al*](http://havlin.biu.ac.il/PS/Quantification%20of%20scaling%20exponents%20and%20crossover%20phenomena%20in%20nonstationary%20heartbeat%20time%20series.pdf). The algorithm involves dividing the integrated RR interval time series into non-overlapping segments of equal length. 

A polynomial is then fitted to each non-overlapping segment. Linear, quadratic, cubic, and/or other higher polynomials may be used in the fitting procedure. These DFA orders differ in their ability to eliminate various types of trends from the time series. Thus, an estimation of the type of time series trend can be captured via comparison of the different DFA orders, as seen below. 


Following the polynomial fit, the average of all the segments are obtained via:

where q is the order of the fluctuation coefficient. When *q* = 2, the MF-DFA procedure simplifies to standard DFA. It may be of the user’s interests to explore how the q-dependent fluctuation coefficients *F_q (s)* depend on scale s for various values of q.

### Multiscale Entropy (MSE)

Costa, Madalena, Ary L. Goldberger, and C-K. Peng. "Multiscale entropy 
analysis of complex physiologic time series." *Physical review letters* 89.6 
(2002): 068102.
