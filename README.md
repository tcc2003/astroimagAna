# AstroImagAna
## Purpose
Enhance the S/N ratio to make the relatively weak line visible.

## Procedure
1. **Read FITS datacube** 
2. **Fit 1D gaussian function**   
    - `curve_fit`
    - `gausspy algorithm`

3. **Remove the Doppler effect**   
    By calculating the changes in frequency and velocity, we can correct for the Doppler effect. Verify the correction by examining the velocity and intensity array plots to ensure the effectiveness of the adjustment.
4. **Stack the spectra**


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
