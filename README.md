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
<br/>
<br/>
# Website Part
## Framework
Our Website is build under Django Framework with Python backend.

## Local Server Build Instruction
Install Django by ```sudo apt-get install python3-django```<br/>
Unzip the file ```proj_web.tar.gz``` and place it where ever you like.
Enter the proj_web dir ```cd ./proj_web/mysite``` <br/>

Some absolute path in the file need to be modified.
In ```./tgs/views.py``` line 85, change the path into the local path of your keras model.

And then, in ```./proj_web/mysite``` run ```python manage.py runserver``` to start the local server.

Open your browser and enter ```localhost:8000/tgs/``` to see the website.
