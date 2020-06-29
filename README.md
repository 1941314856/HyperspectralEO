# HyperspectralEO

## Usage

### process_data.py 

`python process_data.py --dataset PaviaU --sets train,val,test --sensor ROSIS --display visdom`

**Arguments:**
* `--dataset` : *string*
* `--sets` : *string* 
* `--sensor` : *string* 
* `--classes` : *string* 
* `--smooth` : *string* 
* `--remove` : *string* 
* `--apply` : *string* 
* `--n_components` : *int* 
* `--C1` : *int* 
* `--C2` : *int* 
* `--show` : *string* 
percentage of data to show
* `--dataviz` : *string* 
store true to display the data spectrums
* `--save` : *string* 
folder_path where to save the processed data
* `--folder` : *string* 
folder_path where to save the figures
* `--display` : *string* 
display either with 'matplotlib' or 'visdom'
