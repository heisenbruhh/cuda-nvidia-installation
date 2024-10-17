##Steps to install NVIDIA drivers and CUDA on UBUNTU 20.04 focal fossa##

#to purge nvidia completely from system

sudo apt purge nvidia* -y
sudo apt remove nvidia-* -y
sudo rm /etc/apt/sources.list.d/cuda*
sudo apt autoremove -y && sudo apt autoclean -y
sudo rm -rf /usr/local/cuda*

#steps to install nvidia-smi

sudo ubuntu-drivers list

(this should give you a list of driver versions, check which version of driver is required according to the version of cuda you want to install)

sudo ubuntu-drivers install nvidia:535

(here we want to install cuda 12.2 and the compatible nvidia driver for it is 535)

(once installed we need to restart the system)

sudo reboot

(once the system has restarted we can now verify the installation by typing the following)

nvidia-smi

(it should show the following:)

Thu Oct 17 10:03:48 2024       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.183.01             Driver Version: 535.183.01   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA RTX A4000               Off | 00000000:47:00.0  On |                  Off |
| 41%   46C    P2              35W / 140W |    902MiB / 16376MiB |      1%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A       921      G   /usr/lib/xorg/Xorg                           39MiB |
|    0   N/A  N/A      1296      G   /usr/lib/xorg/Xorg                          190MiB |
|    0   N/A  N/A      1422      G   /usr/bin/gnome-shell                         96MiB |
|    0   N/A  N/A      1943      G   ...seed-version=20241015-180122.530000       45MiB |
|    0   N/A  N/A      4232      G   ...erProcess --variations-seed-version       57MiB |
|    0   N/A  N/A    190331      C   ...ktop/huggingface/env/bin/python3.10      448MiB |
+---------------------------------------------------------------------------------------+

#steps to install CUDA

(There are various ways to install cuda, we will follow the local runfile method)

(go to google and type the cuda version you want to install which is compatible with the driver that you just installed)

(for me it is cuda 12.2)

(click on the nvidia link and follwo the steps to install the local runfile of cuda)

(in my case it is)

wget https://developer.download.nvidia.com/compute/cuda/12.2.0/local_installers/cuda_12.2.0_535.54.03_linux.run

(once the file has been downloaded, run the following command:)

sudo sh cuda_12.2.0_535.54.03_linux.run

(follow the instructions)

1. continue
2. accept
3. (make sure to uncheck everything other than the cuda toolkit)
4. youre done...

(to verify the installation run the folllwoing command)

nvcc --version

(it should give the following output:)

nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2023 NVIDIA Corporation
Built on Tue_Jun_13_19:16:58_PDT_2023
Cuda compilation tools, release 12.2, V12.2.91
Build cuda_12.2.r12.2/compiler.32965470_0






