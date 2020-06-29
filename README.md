# HyperspectralEO


### process_data.py 

This script allows the user to process and visualize hyperspectral data. 

#### Usage

`python process_data.py --dataset PaviaU --sets train,val,test --sensor ROSIS --display visdom`

**Arguments:**  
  
 `--dataset` : *string*  
 `--sets` : *string*   
 `--sensor` : *string*   
 Name of the sensor to use. If the specified sensor is not the sensor which acquired the data, then the hyperspectral image will be simulated based on the sensor spectral response and on the GSD.  
 `--classes` : *string*  
 Classes id to select (ex: 1,2,3).     
 `--smooth` : *float*  
 Standard deviation of the gaussian filter to apply on the spectrums.     
 `--remove` : *int*  
 Number of bands to remove at the begining of the spectrums.      
 `--apply` : *string*  
 Analysis to apply (pca or lda).    
 `--n_components` : *int*  
 Number of components to keep.    
 `--C1` : *int*  
 First component to display.    
 `--C2` : *int*  
 Second component to display.    
 `--show` : *string*  
 Percentage of data to show.    
 `--dataviz` : *boolean*  
 Store true to display the data spectrums.    
 `--save` : *string*  
 Folder path where to save the processed data.    
 `--folder` : *string*  
 Folder path where to save the figures.    
 `--display` : *string*  
 Display either with 'matplotlib' or 'visdom'.     
 
 ### plot.py
 
 This scirpt allows the user to select pixels and plot their spectrums.
 
 #### Usage
 
 `python plot.py --dataset PaviaU --sets train,val`
 
 **Arguments:**

 `--dataset` : *string*  
 `--sets` : *string* 
 
 ### select_gt.py
 
 This script allows the user to select a ground truth over some dataset.
 
  **Arguments:**
 
 `--dataset` : *string*  
 `--set` : *string*   
 `--file_path` : *string*    
 File path where to save the ground truth.

 **Returns:**  
 A 2D numpy array ground truth.
