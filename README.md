# simian GPU workstation
Instructions, scripts, and FAQ for the GPU workstation belonging to the Georgia Tech ML Theory Group

If you have problems or questions, please message me on Teams *after reading this entire document*

## Setup instructions
### IMPORTANT: You MUST connect to the workstation using your default Georgia Tech username (e.g. tlabonte3) and NOT your email alias (e.g. tyler)

1. Visit <https://vpn.gatech.edu/> and log in with your Georgia Tech credentials
2. Download and install the appropriate VPN client for your machine (Windows/MacOS in the top right, Linux at the bottom)
3. Log in to the VPN client with your Georgia Tech credentials

#### USERS:
4. Open `simian.cc.gatech.edu` in your browser
5. Log in with your username and password (note: when you log in for the first time, the password you enter will be your new password)
6. Open `simian.cc.gatech.edu/user/[username]/lab` in your browser
7. Click Notebook to use a Jupyter notebook or Terminal to use a terminal

#### ADMINS ONLY:
4. If using Windows, follow [these instructions](https://learn.microsoft.com/en-us/windows/wsl/install) to install WSL
5. Open a terminal on your local machine (via WSL if on Windows)
6. Use the command `ssh [your Georgia Tech username]@simian.cc.gatech.edu` to access the workstation; the password is your Georgia Tech password

## Conda environment instructions
### IMPORTANT: Do NOT install any packages unless you are in a conda environment

#### TERMINAL:
1. Use the command `conda create -n [your environment name] python=[your python version]` to create an Anaconda environment
2. Use the command `conda activate [your environment name]` to enter your Anaconda environment
3. Install packages using `conda` or `pip`

#### JUPYTER:
1. Use the command `conda create -n [your environment name] python=[your python version]` to create an Anaconda environment
2. Use the command `conda activate [your environment name]` to enter your Anaconda environment
3. Use the command `conda install ipykernel` to install the IPython kernel package
4. Use the command `ipython kernel install --user --name=<any_name_for_kernel>` to instantiate your kernel
5. Refresh your Jupyter instance, then select your new kernel from the Kernels tab
6. Install packages using `conda` or `pip`

## Job submission instructions
### IMPORTANT: Do NOT submit a job which overflows the GPU memory -- this will cancel other students' jobs

1. Use the command `nvidia-smi` to check available compute
2. Select GPU 0 or GPU 1 based on the amount of GPU memory available
3. Use the command `CUDA_VISIBLE_DEVICES=[your GPU number] python [your script name]` to submit your job
4. To kill your job prematurely, use `nvidia-smi` to check the process id (make sure it is correct!), then use the command `kill -9 [process id]`

## FAQ
1. Coming soon
