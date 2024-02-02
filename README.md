Step-by-step instructions to install Conda, Jupyter, and MindSpore for the repository https://github.com/kny5/infotec_hcia_ai:

### 1. Install Conda:

#### For Linux/macOS:

```bash
# Download the Miniconda installer
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh

# Run the installer
bash miniconda.sh -b -p $HOME/miniconda

# Add conda to your PATH
echo 'export PATH="$HOME/miniconda/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

#### For Windows:

Download the Miniconda installer from https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe and run the installer.

### 2. Create a Conda environment:

```bash
# Navigate to the repository directory
cd infotec_hcia_ai

# Create a Conda environment
conda create --name infotec_hcia_ai python=3.7

# Activate the environment
conda activate infotec_hcia_ai
```

### 3. Install Jupyter:

```bash
# Install Jupyter
conda install jupyter
```

### 4. Install MindSpore:

```bash
# Install MindSpore (CPU version)
conda install -c mindspore mindspore

# OR Install MindSpore (GPU version, if you have a compatible GPU)
conda install -c mindspore mindspore-gpu
```

### 5. Start Jupyter Notebook:

```bash
# Launch Jupyter Notebook
jupyter notebook
```

This will open Jupyter in your default web browser. You can then navigate to the repository directory in the Jupyter interface and start working with the provided notebooks.

Note: Make sure to adapt these instructions if you are using a specific operating system or have specific requirements. Additionally, verify the MindSpore version compatibility with your system and adjust the installation command accordingly.

### 6. Install mindspore-gpu for Windows Linux Subsystem (WSL2)

To install MindSpore with GPU support on WSL 2 running Ubuntu 20.04 with CUDA 11.1, you can follow these steps:

#### 1. Install CUDA Toolkit 11.1 on WSL 2:

```bash
# Update package information
sudo apt update

# Install basic dependencies
sudo apt install -y build-essential

# Download CUDA Toolkit 11.1 deb (network) installer
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin
sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/11.1.1/local_installers/cuda-repo-ubuntu2004-11-1-local_11.1.1-455.32.00-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu2004-11-1-local_11.1.1-455.32.00-1_amd64.deb
sudo apt-key add /var/cuda-repo-ubuntu2004-11-1-local/7fa2af80.pub
sudo apt-get update
sudo apt-get -y install cuda
```

#### 2. Set up Environment Variables:

Add the following lines to your `~/.bashrc` or `~/.zshrc` file:

```bash
export PATH=/usr/local/cuda-11.1/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-11.1/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

Then, run:

```bash
source ~/.bashrc   # or source ~/.zshrc
```

#### 3. Install cuDNN:

Download cuDNN from the NVIDIA website (requires registration): https://developer.nvidia.com/rdp/cudnn-download

Follow the installation instructions provided on the cuDNN download page.

#### 4. Install MindSpore with GPU support:

```bash
# Install additional dependencies
sudo apt install -y python3-pip libgl1-mesa-glx

# Install MindSpore GPU version
pip3 install https://ms-release.obs.cn-north-4.myhuaweicloud.com/1.7.0/MindSpore/gpu/ubuntu_x86/cuda-11.1/mindspore_gpu-1.7.0-cp38-cp38-linux_x86_64.whl
```

#### 5. Verify Installation:

```bash
# Verify MindSpore installation
python3 -c "import mindspore; print(mindspore.__version__)"
```

This should output the installed MindSpore version.

Now, you have successfully installed MindSpore with GPU support on WSL 2 with Ubuntu 20.04 and CUDA 11.1. Make sure to check the official MindSpore documentation for any updates or changes to the installation process.
