Debian 11 bullseye

```
wget https://developer.download.nvidia.com/compute/cuda/12.1.1/local_installers/cuda_12.1.1_530.30.02_linux.run
sudo apt-get install -y linux-headers-`uname -r`
sudo sh cuda_12.1.1_530.30.02_linux.run --silent --driver --toolkit
```
add this to .bashrc
```
alias python=python3
export PATH="/usr/local/cuda-12.1/bin:$PATH"
export LD_LIBRARY_PATH="/usr/local/cuda-12.1/lib64:$LD_LIBRARY_PATH"
```

```
pip3 install --pre torch torchvision torchaudio --index-url https://download.pytorch.org/whl/nightly/cu121 --force-reinstall
pip uninstall -y xformers && MAX_JOBS=11 pip install -v -U git+https://github.com/facebookresearch/xformers.git@main#egg=xformers
pip install protobuf==3.20.*
pip install tensorboard
pip uninstall deepspeed
pip install deepspeed
pip install scipy
pip install opencv-python
sudo apt-get install -y htop libsm6 libxext6
sudo apt-get install -y libxrender-dev
pip uninstall apex
pip install --upgrade pip setuptools wheel
git clone https://github.com/NVIDIA/apex.git
pip install "numpy<1.24"
pip uninstall -y typing_extensions && pip install typing_extensions==4.7.1
cd apex
pip install -v --disable-pip-version-check --no-cache-dir --no-build-isolation --config-settings "--build-option=--cpp_ext" --config-settings "--build-option=--cuda_ext" ./
```