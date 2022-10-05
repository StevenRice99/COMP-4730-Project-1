# COMP-4730 Project 1

- [Setup](#setup "Setup")
- [Usage](#usage "Usage")
- [References](#references "References")

# Setup

1. Install [Python](https://www.python.org "Python").
   1. Python 3.7.10 was used for this project's creation, but any newer version should work.
2. Install required Python packages. If unfamiliar with Python, "pip" comes with standard Python installations, and you can run "pip *package*" to install a package.
   1. [PyTorch](https://pytorch.org "PyTorch") and TorchVision.
      1. It is recommended you visit [PyTorch's get started page](https://pytorch.org/get-started/locally "PyTorch Get Started") which will allow you to select to install CUDA support if you have an Nvidia GPU. This will give you a command you can copy and run to install PyTorch, TorchVision, and TorchAudio, but feel free to remove TorchAudio from the command as it is not needed.
      2. When running the script, a message will be output to the console if it is using CUDA.
   2. The remaining packages can be installed via "pip *package*" in the console:
      1. [shutil](https://docs.python.org/3/library/shutil.html "shutil")
      2. [tensorboard](https://pypi.org/project/tensorboard "tensorboard")
      3. [torchsummary](https://pypi.org/project/torchsummary "torchsummary")
      4. [torchviz](https://pypi.org/project/torchviz "torchviz")
      5. [tqdm](https://github.com/tqdm/tqdm "tqdm")
3. Install [Graphviz](https://graphviz.org "Graphviz") so the Python script can generate a graph of neural networks.

# Usage

1. Clone or download and extract this repository.
2. Follow [setup](#setup "Setup") steps.
3. "model_builder.py" is where you can build your model architecture.
   1. Since we are working with the MNIST dataset, the input is always 1 channel 28x28, and the final output needs to be 10.
4. In the cloned/downloaded directory, run: **tensorboard --logdir="runs"** or **python -m tensorboard.main --logdir=[PATH_TO_LOGDIR]**
   1. This will allow you to open TensorBoard in your browser which by default is usually at [http://localhost:6006](http://localhost:6006 "Tensorboard").
5. Run "mnist.py" with optional run parameters.
   1. -n, --name - Name of the model. Defaults to "Model".
   2. -e, --epoch - Number of training epochs. Defaults to 5.
   3. -b, --batch - Training and testing batch size. Defaults to 64.
   4. -l, --load - Load the model with the given name and test it.
   5. -c, --count - Count image labels in the MNIST dataset.
   6. --min - Minimum rescaling size of training data. Defaults to 0.
   7. --max - Maximum rescaling size of training data. Defaults to 0.
   8. -r, --rot - Maximum rotation of training data. Defaults to 0.
6. Once done, the model('s) :
   1. Will be saved with the name as it given in the "Models" folder.
   2. Architecture will be saved as a graph in the "Graphs" folder.
   3. Parameters and accuracy will be saved with the same model name in the "ModelParameters" folder. 
   4. TensorBoard data will be saved in the "runs" folder.
   - Note if this run produced a worse accuracy than a previous run which had the same name, it will not be saved to preserve the best model.

# Limitations

- Loading a model will fail if you modified the architecture in "model_builder.py" from when the model you are trying to load was made.

# References

- Initial implementation based on [this video](https://www.youtube.com/watch?v=9Bxf9voEbMg "YouTube Video") for initial PyTorch setup and running on the GPU if available.
