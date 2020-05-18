# TorchvisionObjectDetection
## Introduction
This repository is a study about the [Pytorch Torchvision Object Detection Finetuning Tutorial](https://pytorch.org/tutorials/intermediate/torchvision_tutorial.html). I followed their steps and improved the code, so now we can not only train the model, but it is possible to save it, load it and pass some images in the model, predicting the pedestrians and generating an image mask. The pedestrian databse used was the [Penn-Fudan Database](https://www.cis.upenn.edu/~jshi/ped_html/).
Here, I will explain how to properly run this repo code and I will also provide a simple help guide, showing some errors that I found while trying to make the tutorial work in my computer. So let's get started.

## Windows 10 Setup Guide
This is the setup guide for the code that can be found in this repo. Just follow these steps and you should be ready to run it.
* First install [Anaconda](https://www.anaconda.com/);
* Open Anaconda 3 terminal and install [numpy](https://scipy.org/install.html#pip-install), it is an important dependency; 
* Install cython with `pip install cython`;
* Install PyTorch and Torchvision using the Anaconda terminal. You can get the proper install command in the [PyTorch official website](https://pytorch.org/). In my case, the proper command to use was: `conda install pytorch torchvision cudatoolkit=10.2 -c pytorch`;
* *OPTIONAL* You may run the example in the [PyTorch Get Started Locally](https://pytorch.org/get-started/locally/) to test if everything is properly installed;
* Now, you may clone this repo to your computer and run it. Have Fun! 
* **OBS:** If you are experiencing some errors, try checking the Windows 10 Simple Help Guide bellow, It contains some errors that I experienced and how to solve them.
* **OBS 2:** Don’t forget to change the variables `path` in the `tv-training-code.py` and in the `tv-evaluation-code.py`, at the end of the code, to correspond to the proper paths you want to use.

## Windows 10 Simple Help Guide
In case you want to follow the tutorial for yourself, and just use this repository as some kind of help, here are some tips. 
I suggest that you follow the Setup Guide above, because it contains the same dependencies that you will need in the tutorial.

### Possible Errors
While trying to make things work in your computer you may find some annoying errors. Here are some of the errors i found and how to solve them.
* *Error: Microsoft Visual C++ 14.0 is required*. While trying to install pycocotools. It may say it doesn’t work in Windows (but be cool, it will!)
  * To solve this error, I installed the [Microsoft Visual Studio](https://visualstudio.microsoft.com/visual-cpp-build-tools/), selecting the V14 from 2015 on the right column, just like shown in this [Medium article](https://medium.com/@jacky_ttt/day060-fix-error-microsoft-visual-c-14-0-is-required-629413e798cd);
* In case you have some *Coco API errors*, try cloning this [repository](https://github.com/cocodataset/cocoapi.git) in the root folder of the project (This files are already here in this repo)
* *Error: import pycocotools._mask as _mask ModuleNotFoundError: No module named 'pycocotools._mask'*
  * To solve it, I accessed this [repository](https://github.com/philferriere/cocoapi) and followed the readme instructions. Long story short, i just deleted the pycocotools directory from the root folder and then i installed them via pip, like the following command: `pip install git+https://github.com/philferriere/cocoapi.git#subdirectory=PythonAPI`
* *Error: AssertionError: Torch not compiled with CUDA enabled*
  * There can be some reasons why you are getting this error:
    * You may not have CUDA installed, so download and install [CUDA](https://developer.nvidia.com/cuda-downloads?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exelocal);
    * You may not have installed Pytorch and Torchvision properly. Try checking out the installation running this command in your Anaconda Terminal: `conda list | findstr "torch"`. If your results says something about *[cpuonly]*, then the installation is wrong. In this case, try removing all these torch packages and reinstall them with the CUDA Toolkit, using the [PyTorch Official Website](https://pytorch.org/) to check which command suits you better.
    * You may have everything installed correctly, but the code is still trying to run things in the CPU (silly code). Try adding a line `model.cuda()` before executing your model.

I hope this Simple Help Guide helped you in some way. Enjoy the code.
