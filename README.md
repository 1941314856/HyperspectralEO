# HyperspectralEO


### process_data.py 

.This script allows the user to process and visualize hyperspectral data. 

#### Usage

`python process_data.py --dataset PaviaU --sets train,val,test --sensor ROSIS --display visdom`

**Arguments:**  
  
 `--dataset` : *string*  
 `--sets` : *string*   
 `--sensor` : *string*   
 `--classes` : *string*  
 classes id to select (ex: 1,2,3)   
 `--smooth` : *float*  
 standard deviation of the gaussian filter to apply on the spectrums   
 `--remove` : *int*  
 number of bands to remove at the begining of the spectrums    
 `--apply` : *string*  
 analysis to apply (pca or lda)  
 `--n_components` : *int*  
 number of components to keep  
 `--C1` : *int*  
 first component to display  
 `--C2` : *int*  
 second component to display  
 `--show` : *string*  
 percentage of data to show  
 `--dataviz` : *boolean*  
 store true to display the data spectrums  
 `--save` : *string*  
 folder path where to save the processed data  
 `--folder` : *string*  
 folder path where to save the figures  
 `--display` : *string*  
 display either with 'matplotlib' or 'visdom'  
