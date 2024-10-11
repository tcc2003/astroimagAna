# Line Stacking Technique
## Purpose
Enhance the S/N ratio to make the relatively weak line visible.

## Procedure
1. **Read FITS datacube**    
    Loading the FITS data by `Astropy`.
2. **Fit 1D gaussian function**   
    - `curve_fit`: A standard method for fitting 1D polynomial function in Python. However, it may encounter significant challenges due to uncertainties in initial parameter values, imperfect data, or data with large     
 separations.
    - `GaussPy package`(Lindner et al. 2015): Utilizes derivative spectroscopy and Tikhonov regularization to determine the Gaussian components and deblend the amplitude guesses. The user must first train the AGD algorithm to obtain the optimal smoothing parameters for the derivatives.This method is particularly effective for spectra with multiple Gaussian components (see directory gausspy_fit).

3. **Remove the Doppler shift**   
    Correct for the Doppler effect by calculating the changes in frequency and velocity. The effectiveness of the correction will be verified by analyzing the velocity and intensity array plots, ensuring that the adjustment has been accurately applied.
4. **Stack the spectra**   
    By removing the Doppler shift in each pixel, all emissions can be aligned with systematic velocities and stacked subsequently.


## Instruction
Ensure that all necessary dependencies are installed. Before installation, use `Anaconda3` to manage the development environment. You can type:   
```
conda create --name astroimgAna python=3.7        
pip install --upgrade pip      
pip install numpy scipy pandas matplotlib   
pip install astropy==4.3.1   
pip install aplpy==2.0.3     
pip install jupyter   
pip install h5py   
pip install PyAVM healpy
```   

   

## Reference
Linder, R. R., et al. 2015, ApJ, 149:138 
