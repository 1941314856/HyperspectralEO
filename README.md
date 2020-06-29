# HyperspectralEO

### main.py

This script allows the user to train and evaluate machine learning models for hyperspectral images classification.

#### Usage 

`python main.py --dataset PaviaU --model nn --train --epoch 200 --classes 1,2 `  

**Arguments:**  

 `--dataset` : *string*  
 `--model` : *string*  
 `--runs` : *string*  
 `--restore` : *string*  
 `--train` : *string*  
 `--test` : *string*  
 `--map` : *string*  
 `--res_folder` : *string*  
 `--visdom` : *string*  
 `--summary` : *string*  
 `--one_vs_all` : *string*  
 `--classes` : *string*  
 `--epoch` : *string*  
 `--patch_size` : *string*  
 `--lr` : *string*  
 `--weight_decay` : *string*  
 `--batch_size` : *string*  
  `--test_stride` : *string*  
 `--flip_augmentation` : *string*  
 `--radiation_augmentation` : *string*  
 `--mixture_augmentation` : *string*  
  


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
 
 #### Usage  
 
 `python select_gt.py --dataset PaviaU --set train --file_path file_path`  
 
  **Arguments:**
 
 `--dataset` : *string*  
 `--set` : *string*   
 `--file_path` : *string*    
 File path where to save the ground truth.

 **Returns:**  
 A 2D numpy array ground truth.
