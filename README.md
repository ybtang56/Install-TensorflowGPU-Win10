# Install-TensorflowGPU-Win10
Summarize the way to install Tensorflow GPU on windows 10 machine.

In windows 10, the tensorflow-gpu will cause some errors if it is installed via `pip install tensorflow-gpu` command. 
This is because in win10, the default tensorflow-gpu version is 1.12.0, where the required cuda version must be v9.0 rather than the latest one v10.0. 

Please beaware the **Software requirements** from the official site: https://www.tensorflow.org/install/gpu

## Softwaare requriments:
1. NVIDIA® GPU drivers —CUDA 9.0 requires 384.x or higher. https://www.nvidia.com/drivers
2. CUDA® Toolkit —TensorFlow supports CUDA 9.0. https://developer.nvidia.com/cuda-zone
3. cuDNN SDK (>= 7.2) https://developer.nvidia.com/cudnn
  + it's a zipped file folder. unzip and copy it under 'C:\tools\cudnn90\' location. 
  + Copy the file `C:\tools\cudnn90\bin\udnn64_7.dll` to `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\bin` (**<==Very IMPORTANT!!!**)
4. pip install tensorflow-gpu

## Windows Configurations
```bash
SET PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\bin;%PATH%
SET PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\extras\CUPTI\libx64;%PATH%
SET PATH=C:\tools\cudnn90\bin;%PATH%
```

## test the tensorflow-gpu
running below commands in python or python3:
```python
from tensorflow.python.client import device_lib
print(device_lib.list_local_devices())
```
