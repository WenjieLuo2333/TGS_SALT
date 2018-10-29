# TGS_SALT
## Build instruction<br/>
All the codes and comments are in a single jupyter notebook filr named ```kernel.py```.<br/>
Build with ```numpy```,```keras```,```tensorflow```,```pandas```<br/>
Highly recommend to run jupyter notebook file on [Kaggle Kernel](https://www.kaggle.com/wenjieluo/tgs-wj). Just sign up and fork the notebook and then it's easy to run it with Kaggle Kernel's build in environment and GPU is provided.<br/>
## Data Set
Please download data from [here](https://www.kaggle.com/c/tgs-salt-identification-challenge/data).<br/>
## Trainning Strategy<br/>
### model<br/>
Unet-like Structure with Resnet Model<br/>
Input resize from 101\*101 to 128\*128.<br/>
Batch normalization,dropout and shortcut connection are used to improve the performance of the typical U-net.<br/>

### Augmentations<br/>
flip images vertically and horizontally to enlarge datasets.<br/>

### Optimizer<br/>
Build in Adam optimizer<br/>
```reduce_lr = ReduceLROnPlateau(factor=0.1, patience=5, min_lr=0.00001, verbose=1)```<br/>
```epochs = 200```<br/>
```batch_size = 32```<br/>
```early_stopping = EarlyStopping(patience=10, verbose=1)```<br/>
### Loss<br/> 
mean-IOU<br/>
### Accuracy and loss for train and validation<br/>
![alt text](https://github.com/WenjieLuo2333/TGS_SALT/blob/master/__results___28_0.png)<br/>
Blue for training and yellow for validation.<br/>
### Best Accuracy
Best Accuracy is at 77.6%.
