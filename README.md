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

## Dependencies

0. Common
Set up virtual environment for Python using Anaconda [](https://docs.anaconda.com/anaconda/install/linux/)

```Shell
sudo apt install curl --yes
```
# Download Anaconda
```Shell
cd ~ && curl -O https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh
```
# Install Anaconda
```Shell
bash Anaconda3-2024.06-1-Linux-x86_64.sh
>>> yes 
```
# Once the installation is completed, close and reopen the shell to confirm the changes took effect.
# Update the system's PATH variable.
```Shell
source ~/.bashrc
```
2. PyTorch

3. SMPL-X

4. VPoser

5. SMPLify-X
   
## References

