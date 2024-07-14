## SMPLify-X: Expressive Body Capture: 3D Hands, Face, and Body from a Single Image

[[Project Page](https://smpl-x.is.tue.mpg.de/)] 
[[Paper](https://ps.is.tuebingen.mpg.de/uploads_file/attachment/attachment/497/SMPL-X.pdf)]
[[Supp. Mat.](https://ps.is.tuebingen.mpg.de/uploads_file/attachment/attachment/498/SMPL-X-supp.pdf)]

## Fitting

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
where the `../data` should contain two subfolders, *images*, where the images are located, and *keypoints*, where the OpenPose output should be stored.

## Set up 

### 0. Virtual environment for Python, [reference](https://phoenixnap.com/kb/install-anaconda-ubuntu)
```Shell
# Update the latest available package versions
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

# Activate the virtual environment
conda activate $PATH_TO_VENV
```

**Just do it in case the virtual environment goes wrong!!!**
```Shell
# Deactivate the virtual environment
conda deactivate

# Delete the virtual environment
conda remove -p $PATH_TO_VENV --all
```

### 1. PyTorch, [reference](https://stackoverflow.com/questions/60987997/why-torch-cuda-is-available-returns-false-even-after-installing-pytorch-with/61034368#61034368)

* Update the newest GPU driver using Software Updater

* The GPU on my system is GeForce GT 730 -> Compute Capability is 3.5. This is a long trial and error process to figure out which pytorch version is suitable for my GPU. Finally I went for pytorch **1.1.0** as the higher version don't support this GPU

```Shell
# CUDA 10.0
conda install pytorch==1.1.0 torchvision==0.3.0 cudatoolkit=10.0 -c pytorch
```

### 2. SMPL-X

```Shell
pip install smplx[all]
cd ~ && git clone https://github.com/reenor/smplx
cd ~/smplx && python setup.py install
cd ~ && rm -rf smplx
```

### 3. VPoser

There are two models: vposer_v1_0 and vposer_v2_0. As vposer_v2_0 requires pytorch 1.7, I choose installing vposer_v1_0

```Shell
# Install dependencies
pip install git+https://github.com/reenor/configer

# Install vposer_v1_0
pip install git+https://github.com/reenor/human_body_prior@cvpr19#egg=human_body_prior
```

### 4. SMPLify-X

```Shell
mkdir -p $PATH_TO_PROJECT && cd $PATH_TO_PROJECT
git clone https://github.com/reenor/smplify-x
cd $PATH_TO_SMPLIFY_X
pip install -r requirements.txt
```

### 5. Pre-built models SMPL-X and VPoser

```Shell
mkdir -p $PATH_TO_PROJECT/smplx/models_smplx_v1_1 $PATH_TO_PROJECT/vposer
```

* Download SMPL-X model (models_smplx_v1_1.zip, ~830MB) from [[Project Page](https://smpl-x.is.tue.mpg.de/)] and copy it to folder $PATH_TO_PROJECT/smplx/models_smplx_v1_1

* Download VPoser model (vposer_v1_0.zip, ~ 2.5MB) and copy it to folder $PATH_TO_PROJECT/vposer

```Shell
unzip -n $PATH_TO_PROJECT/smplx/models_smplx_v1_1/models_smplx_v1_1.zip -d $PATH_TO_PROJECT/smplx/models_smplx_v1_1
unzip -n $PATH_TO_PROJECT/vposer/vposer_v1_0.zip -d $PATH_TO_PROJECT/vposer
```
   
## References

