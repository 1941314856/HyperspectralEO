# HyperspectralEO

HyperspectralEO is a toolbox built on https://github.com/nshaud/DeepHyperX/ to process, analyze and classify hyperspectral / multispectral images with a special focus on impervious surfaces classification.

## models.py

Basic neural networks and state-of-the-art deep networks are implemented in PyTorch in this script:
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
  
  Basic FNN or 1D CNN can be easily implemented with various architectures by initializing the `FNN` or `CNN1D` classes with such params:   
  `  {1:{'h1': 8, 'h2':128, 'activation': F.relu, 'dropout': 0},
      2:{'h1': 128, 'h2':256, 'activation': F.relu, 'dropout': 0},
      3:{'h1': 256, 'h2':128, 'activation': F.relu, 'dropout': 0},
      4:{'h1': 128, 'h2':14, 'activation': lambda x: x, 'dropout': 0}}`
  
## data.py

This script defines a `Dataset` class that represents a hyperspectral scene. A `Dataset` has various attributes such as:  
* `IMG`: a *dictionnary* containing the spectrums as 3D numpy arrays for the training, validation and test sets  
* `GT`: a *dictionnary* containing the ground truth as 2D numpy arrays for the training, validation and test sets  
* `label_values`: the names of the classes  
* `sensor`: a `Sensor` object that represents a spectral sensor
  
## datasets.py 

This script configures available datasets : 
* Pavia Center  
* Pavia University 
* Salinas  
* Indian Pines 
* Botswana
* Kennedy Space Center 
* Fauga

## sensors.py 

Sensors are configured in this script. A `Sensor` object has various attributes such as:  
* `wavelengths`: a *list* of each band wavelength  
* `n_bands`: *int*, the number of usable bands 
* `rgb_bands`: a *tuple* of the rgb bands for display

## create_sets.py

This script allows the user to create disjoint train, validation and test sets from a hyperspectral scene.
 
#### Usage

`python create_sets.py --dataset PaviaU --training_sample 60 --val_sample 50 --sampling_mode disjoint`

60% of samples will constitute the train set, 20 % the validation set and 20 % the test set. When `--download` argument is used, the specified dataset is download from the source configured in datasets.py 

## process_data.py 

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
 
 ## plot.py
 
 This scirpt allows the user to select pixels and plot their spectrums on visdom.
 
 #### Usage
 
 `python plot.py --dataset PaviaU --sets train,val`
 
 **Arguments:**

 `--dataset` : *string*  
 `--sets` : *string* 
 
 ## select_gt.py
 
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

## main.py

This script allows the user to train and evaluate machine learning models for hyperspectral classification.

#### Usage 

`python main.py --dataset PaviaU --model nn --train --epoch 200 --classes 1,2 `  

**Arguments:**  

 `--dataset` : *string*  
 `--model` : *string*  
 `--cuda` : *int*  
 CUDA device (CPU or GPU).    
 `--runs` : *int*  
 Number of runs.  
 `--restore` : *string*    
 File path to trained model.    
 `--train` : *boolean*   
 Set to True to train the model.  
 `--test` : *boolean*   
 Set to True to evaluate the model.  
 `--map` : *string*    
 Specified sets over which create map. 
 `--perviousness` : *string*  
 If 'dataset', then converts the ground truth in perviousness classes before training.  
 If 'classification', then converts the prediction in perviousness classes after the materials classification.
 If 'transfer_learning', then the network will be trained to classify materials and perviousness simultaneously according to the `perviousness_classification` function defined in `transfer_learning.py`.  
 `--res_folder` : *string*    
 Folder path where to save the results.    
 `--visdom` : *boolean*  
 True in order to display on visdom.    
 `--summary` : *boolean*   
 True in order to display the dataset summary (nb of classes, pixels...).    
 `--one_vs_all` : *int*  
 If a class id is specified, the dataset will be turned in a One VS All configuration.  
 `--classes` : *string*  
 Classes to keep, for instance '1,2,3'.  
 `--transfer_learning` : *string*  
 Path to pre-trained weights. When specified, the script calls a `transfer_learning` function that has to be designed by your own in `transfer_learning.py`.  
 `--epoch` : *int*    
 `--patch_size` : *int*  
 Neigbourhood size for spatial convolutions.    
 `--lr` : *float*  
 Learning rate for gradient descent.    
 `--weight_decay` : *float*  
 Coeffiicent for L1 regularization.  
 `--class_balancing` : *boolean*  
 Computes inverse median frequency weights if True for neural networks.  
 Random selection of samples to obtain a balanced training set if True for SVM.    
 `--batch_size` : *int*  
  `--test_stride` : *int*  
  `--metrics` : *string*  
  Training and test metrics such as 'OA,kappa,f1_score'.    
 `--flip_augmentation` : *boolean*  
 Random flips if patch_size is superior to 1.  
 `--radiation_augmentation` : *boolean*  
 Random radiation noise to simulate illumination differences.  
 `--mixture_augmentation` : *boolean*  
 Random mixes between spectra.
 
 ## generate.py 
 
 This script allows the user to generate hyperspectral spectrums.
 
 #### Usage 
 
 `python generate.py --hyp_dataset Fauga_FENIX --multi_dataset Fauga_WV3 --clf_model nn --clf_checkpoint nn_path`  
 
 **Arguments:**  
 
 `--hyp_dataset` : *string*  
 Hyperspectral dataset.  
 `--multi_dataset` : *string*  
 Multispectral dataset.    
 `--clf_model` : *string*  
 Hyperspectral classifier.  
 
 Other arguments are the same than main.py arguments.  
 
 ## train_models.py  
 
 This script defines the classes that are used for training and prediction, such as `Train` and `Watch`.
