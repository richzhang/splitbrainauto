# Split-Brain Autoencoders
### Unsupervised Learning by Cross-Channel Prediction
[Richard Zhang](https://richzhang.github.io/), [Phillip Isola](http://web.mit.edu/phillipi/), [Alexei A. Efros](http://www.eecs.berkeley.edu/~efros/). In ArXiv, 2016.

<img src="http://richzhang.github.io/index_files/cvpr2017_splitbrain.png" height="180" />

### Overview ###
This repository contains a test time demonstration using a pre-trained Split-Brain Autoencoder network. The network is a feature extractor using the AlexNet architecture, trained in an unsupervised manner.

### Clone this repository ###
Clone the master branch of the respository using `git clone -b master --single-branch https://github.com/richzhang/splitbrainauto.git`

### Dependencies ###
This code requires a working installation of [Caffe](http://caffe.berkeleyvision.org/). For guidelines and help with installation of Caffe, consult the [installation guide](http://caffe.berkeleyvision.org/) and [Caffe users group](https://groups.google.com/forum/#!forum/caffe-users).

### Test-Time Usage ###
**(1)** Run `./train/fetch_models.sh`. This will load model `model_splitbrainauto_clcl.caffemodel` into the `models` directory.

**(2a)** **Color conversion outside of prototxt** To extract features with the main branch of [Caffe](http://caffe.berkeleyvision.org/): <br>
**(i)** Load the weights `model_splitbrainauto_clcl.caffemodel` with model definition file `deploy_lab.prototxt` in the `models` directory. The input is blob `data_lab`, which is an ***image in Lab colorspace***. You will have to do the Lab color conversion pre-processing outside of the network.

**(2b)** **Color conversion in prototxt** You can also extract features with in-prototxt color version with a modified Caffe. <br>
**(i)** Run `./train/fetch_caffe.sh`. This will load a modified Caffe into directory `./caffe-colorization`. <br>
**(ii)** Install the modified Caffe. For guidelines and help with installation of Caffe, consult the [installation guide](http://caffe.berkeleyvision.org/) and [Caffe users group](https://groups.google.com/forum/#!forum/caffe-users). <br>
**(iii)** Load the weights `model_splitbrainauto_clcl.caffemodel` with model definition file `deploy.prototxt` in the `models` directory. The input is blob `data`, which is a ***non mean-centered BGR image***.

### Citation ###
If you find this model useful for your resesarch, please use this [bibtex](http://richzhang.github.io/index_files/bibtex_arxiv2016_splitbrain.txt) to cite.
 
