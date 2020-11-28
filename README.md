In this assignment you will practice writing backpropagation code, and training
Neural Networks and Convolutional Neural Networks. The goals of this assignment
are as follows:

- understand the architecture of **Convolutional Neural Networks** and train
  gain experience with training these models on data

## Setup
You can work on the assignment in one of two ways: locally on your own machine, or on a virtual machine on Google Cloud.

### Working remotely on Google Cloud (Recommended)

**Note:** after following these instructions, make sure you go to **Working on the assignment** below (you can skip the **Working locally** section).

As part of this course, you can use Google Cloud for your assignments. We recommend this route for anyone who is having trouble with installation set-up, or if you would like to use better CPU/GPU resources than you may have locally. 

Please see the Google Cloud GPU set-up tutorial [here](http://cs231n.github.io/gce-tutorial-gpus/) for instructions. 

We strongly, strongly recommend using Google Cloud with GPU support for the last part of this assignment (the TensorFlow or PyTorch notebooks), since your training will go much, much faster. :)

### Working locally
Here's how you install the necessary dependencies:

**(OPTIONAL) Installing GPU drivers:**
If you choose to work locally, you are at no disadvantage for the first 3 parts of the assignment. For the last part, which is in TensorFlow or PyTorch, however, having a GPU will be a significant advantage. We recommend using a Google Cloud Instance with a GPU, at least for this part. If you have your own NVIDIA GPU, however, and wish to use that, that's fine -- you'll need to install the drivers for your GPU, install CUDA, install cuDNN, and then install either [TensorFlow](https://www.tensorflow.org/install/) or [PyTorch](http://pytorch.org/). You could theoretically do the entire assignment with no GPUs, though this will make training much slower in the last part. 

**Installing Python 3.5+:**
To use python3, make sure to install version 3.5 or 3.6 on your local machine. If you are on Mac OS X, you can do this using [Homebrew](https://brew.sh) with `brew install python3`. You can find instructions for Ubuntu [here](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-ubuntu-16-04).

**Virtual environment:**
If you decide to work locally, we recommend using [virtual environment](http://docs.python-guide.org/en/latest/dev/virtualenvs/) for the project. If you choose not to use a virtual environment, it is up to you to make sure that all dependencies for the code are installed globally on your machine. To set up a virtual environment, run the following:

```bash
cd assignment2
sudo pip install virtualenv      # This may already be installed
virtualenv -p python3 .env       # Create a virtual environment (python3)
source .env/bin/activate         # Activate the virtual environment
pip install -r requirements.txt  # Install dependencies
# Note that this does NOT install TensorFlow or PyTorch, 
# which you need to do yourself.

# Work on the assignment for a while ...
# ... and when you're done:
deactivate                       # Exit the virtual environment
```

Note that every time you want to work on the assignment, you should run `source .env/bin/activate` (from within your `assignment2` folder) to re-activate the virtual environment, and `deactivate` again whenever you are done.

## Working on the assignment:
Get the code as a zip file [here](http://cs231n.stanford.edu/assignments/2017/spring1617_assignment2.zip).

### Download data:
Once you have the starter code (regardless of which method you choose above), you will need to download the CIFAR-10 dataset.
Run the following from the `assignment2` directory:

```bash
cd cs231n/datasets
./get_datasets.sh
```

### Start IPython:
After you have the CIFAR-10 data, you should start the IPython notebook server from the
`assignment2` directory, with the `jupyter notebook` command. (See the [Google Cloud Tutorial](http://cs231n.github.io/gce-tutorial/) for any additional steps you may need to do for setting this up, if you are working remotely)

If you are unfamiliar with IPython, you can also refer to our
[IPython tutorial](/ipython-tutorial).

### Some Notes
**NOTE 1:** This year, the `assignment2` code has been tested to be compatible with python versions `3.5` and `3.6` (it may work with other versions of `3.x`, but we won't be officially supporting them). For this assignment, we are NOT officially supporting python2. Use it at your own risk. You will need to make sure that during your `virtualenv` setup that the correct version of `python` is used. You can confirm your python version by (1) activating your virtualenv and (2) running `which python`.

**NOTE 2:** If you are working in a virtual environment on OSX, you may *potentially* encounter
errors with matplotlib due to the [issues described here](http://matplotlib.org/faq/virtualenv_faq.html). In our testing, it seems that this issue is no longer present with the most recent version of matplotlib, but if you do end up running into this issue you may have to use the `start_ipython_osx.sh` script from the `assignment1` directory (instead of `jupyter notebook` above) to launch your IPython notebook server. Note that you may have to modify some variables within the script to match your version of python/installation directory. The script assumes that your virtual environment is named `.env`.



### Convolutional Networks
In the IPython Notebook ConvolutionalNetworks.ipynb you will implement several new layers that are commonly used in convolutional networks.


For visual recognition tasks, CNNs are undoubtedly the most brilliant. 
What are the advantages of CNNs?

1)Its weight sharing and local connection characteristics make it more like a biological neural network.

2)It makes the computation more efficient and parameters that need training sharply reduced (exponentially).

3)CNNs have powerful feature extraction capabilities (from the edge to the local to the whole)


