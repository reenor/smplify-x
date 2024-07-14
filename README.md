## SMPLify-X: Expressive Body Capture: 3D Hands, Face, and Body from a Single Image

[[Project Page](https://smpl-x.is.tue.mpg.de/)] 
[[Paper](https://ps.is.tuebingen.mpg.de/uploads_file/attachment/attachment/497/SMPL-X.pdf)]
[[Supp. Mat.](https://ps.is.tuebingen.mpg.de/uploads_file/attachment/attachment/498/SMPL-X-supp.pdf)]

## Description

This repository contains the fitting code used for the experiments in [Expressive Body Capture: 3D Hands, Face, and Body from a Single Image](https://smpl-x.is.tue.mpg.de/).

### Fitting
Run the following command to execute the code:
```Shell
python smplifyx/main.py --config cfg_files/fit_smplx.yaml \
    --data_folder  ../data \
    --output_folder ../data/smplifyx_results \
    --visualize=True \
    --gender="male" \
    --model_folder ../smplx/models_smplx_v1_1/models \
    --vposer_ckpt ../vposer/vposer_v1_0 \
    --part_segm_fn ../smplx_parts_segm.pkl
```
where the `../data` should contain two subfolders, *images*, where the
images are located, and *keypoints*, where the OpenPose output should be
stored.

## Set up 

### 0. Virtual environment for Python, [reference](https://phoenixnap.com/kb/install-anaconda-ubuntu)

Update the latest available package versions
```Shell

sudo apt update

# Install the newest versions of all packages currently installed on the system
sudo apt upgrade

sudo apt install git --yes
sudo apt install curl --yes
```

```Shell
# Download Anaconda
cd ~ && curl -O https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh
```

```Shell
# Install Anaconda
bash Anaconda3-2024.06-1-Linux-x86_64.sh
>>> yes >>> yes >>> yes
```

```Shell
# Once the installation is completed, close and reopen the shell to confirm the changes took effect
# Update the system's PATH variable
source ~/.bashrc
```

```Shell
# Initialize shell variables
PATH_TO_VENV=~/venvs/smplify-x
PATH_TO_PROJECT=~/Projects
PATH_TO_SMPLIFY_X=~/Projects/smplify-x
```

```Shell
# Create the virtual environment
conda create -p $PATH_TO_VENV python=3.7 # python 3.8 cannot be used to install pytorch 1.1.0
```

```Shell
# Activate the virtual environment
conda activate $PATH_TO_VENV
```

### 2. PyTorch

### 3. SMPL-X

### 4. VPoser

### 5. SMPLify-X
   
## References

