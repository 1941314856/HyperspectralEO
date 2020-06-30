# HyperspectralEO

### models.py

Classic neural networks and state-of-the-art deep networks are implemented in PyTorch here:   
  * 1D CNN ([Deep Convolutional Neural Networks for Hyperspectral Image Classification, Hu et al., Journal of Sensors 2015](https://www.hindawi.com/journals/js/2015/258619/))
  * Semi-supervised 1D CNN ([Autoencodeurs pour la visualisation d'images hyperspectrales, Boulch et al., GRETSI 2017](https://delta-onera.github.io/publication/2017-GRETSI))
  * 2D CNN ([Hyperspectral CNN for Image Classification & Band Selection, with Application to Face Recognition, Sharma et al, technical report 2018](https://lirias.kuleuven.be/bitstream/123456789/566754/1/4166_final.pdf))
  * Semi-supervised 2D CNN ([A semi-supervised Convolutional Neural Network for Hyperspectral Image Classification, Liu et al, Remote Sensing Letters 2017](https://www.tandfonline.com/doi/abs/10.1080/2150704X.2017.1331053))
  * 3D CNN ([3-D Deep Learning Approach for Remote Sensing Image Classification, Hamida et al., TGRS 2018](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8344565))
  * 3D FCN ([Contextual Deep CNN Based Hyperspectral Classification, Lee and Kwon, IGARSS 2016](https://arxiv.org/abs/1604.03519))
  * 3D CNN ([Deep Feature Extraction and Classification of Hyperspectral Images Based on Convolutional Neural Networks, Chen et al., TGRS 2016](http://elib.dlr.de/106352/2/CNN.pdf))
  * 3D CNN ([Spectral–Spatial Classification of Hyperspectral Imagery with 3D Convolutional Neural Network, Li et al., Remote Sensing 2017](http://www.mdpi.com/2072-4292/9/1/67))
  * 3D CNN ([HSI-CNN: A Novel Convolution Neural Network for Hyperspectral Image, Luo et al, ICPR 2018](https://arxiv.org/abs/1802.10478))
  * Multi-scale 3D CNN ([Multi-scale 3D Deep Convolutional Neural Network for Hyperspectral Image Classification, He et al, ICIP 2017](https://ieeexplore.ieee.org/document/8297014/))
  
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
