# simian GPU workstation
Instructions, scripts, and FAQ for the GPU workstation belonging to the Georgia Tech ML Theory Group

If you have problems or questions, please message me on Teams *after reading this entire document*

## Setup instructions
### IMPORTANT: You MUST connect to the workstation using your default Georgia Tech username (e.g. tlabonte3) and NOT your email alias (e.g. tyler)

#### VPN:
1. Visit <https://vpn.gatech.edu/> and log in with your Georgia Tech credentials
2. Download and install the appropriate VPN client for your machine (Windows/MacOS in the top right, Linux at the bottom)
3. Log in to the VPN client with your Georgia Tech credentials

#### USERS:
1. Install the VPN as above
2. Open `simian.cc.gatech.edu` in your browser
3. Log in with your username and password (note: when you log in for the first time, the password you enter will be your new password)
4. Open `simian.cc.gatech.edu/user/[username]/lab` in your browser
5. Click Notebook to use a Jupyter notebook or Terminal to use a terminal

#### ADMINS ONLY:
1. Install the VPN as above
2. If using Windows, follow [these instructions](https://learn.microsoft.com/en-us/windows/wsl/install) to install WSL
3. Open a terminal on your local machine (via WSL if on Windows)
4. Use the command `ssh [your Georgia Tech username]@simian.cc.gatech.edu` to access the workstation; the password is your Georgia Tech password

## Conda environment instructions
### IMPORTANT: Do NOT install any packages unless you are in a conda environment

#### TERMINAL:
1. Open a terminal, use the command `conda init bash`, and restart your terminal (you only need to do this the first time)
2. Use the command `conda create -n [your environment name] python=[your python version]` to create a conda environment
3. Use the command `conda activate [your environment name]` to enter your conda environment
4. Install packages using `conda` or `pip`

#### JUPYTER:
1. Open a terminal and follow the previous steps
2. Use the command `conda install ipykernel` to install the IPython kernel package
3. Use the command `ipython kernel install --user --name=[your kernel name]` to instantiate your kernel
4. Refresh your browser page, then select your new kernel from the Kernels tab

## Job submission instructions
### IMPORTANT: Do NOT submit a job which overflows the GPU memory -- this will cancel other students' jobs

1. Use the command `nvidia-smi` to check available compute
2. Select GPU 0 or GPU 1 based on the amount of GPU memory available
3. Use the command `CUDA_VISIBLE_DEVICES=[your GPU number] python [your script name]` to submit your job
4. To kill your job prematurely, use `nvidia-smi` to check the process id (make sure it is correct!), then use the command `kill -9 [process id]`

## FAQ
Q1. I'm an admin trying to modify the base conda environment (e.g., to update conda) but it says I don't have permission

A1. Retry the command with `sudo env "PATH=$PATH"` preprended; this is because opt/anaconda3 is not added to the sudo PATH by default

Q2. I'm an admin trying to modify the JupyterLab conda environment, but changes I made when ssh'ed to the machine aren't showing up

A2. The JupyterLab uses a different conda install than the regular machine (/opt/anaconda3 vs opt/tljh); you have to make changes as a JupyterLab admin
