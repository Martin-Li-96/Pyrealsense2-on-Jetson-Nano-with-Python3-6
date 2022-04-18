# Pyrealsense2-on-Jetson-Nano-with-Python3-6
How to install pyrealsense2 on Jestson Nano with Python3.6
The goal of this article is to record how I install the pyrealsense2 on my Jetson nano with Python3.6 
The Intel SDK version is 2.50.0

1. Install the driver of D435i, https://dev.intelrealsense.com/docs/nvidia-jetson-tx2-installation. Use apt method.
2. Download the "librealsense" at https://github.com/IntelRealSense/librealsense/releases/
3. Go to the root directory of the librealsense. "cd XXX/librealsense".
4. Edit the CMakeLists.txt in order to use CUDA. Open this file, and add "set(CMAKE_CUDA_COMPILER /usr/local/cuda/bin/nvcc)" in below 
   "cmake_minimum_required(VERSION 3.1.0)".
5. sudo mkdir build && cd build
6. cmake ../ -DFORCE_RSUSB_BACKEND=ON -DBUILD_PYTHON_BINDINGS:bool=true -DPYTHON_EXECUTABLE=/usr/bin/python3 -DCMAKE_BUILD_TYPE=release -DBUILD_EXAMPLES=true -DBUILD_GRAPHICAL_EXAMPLES=true -DBUILD_WITH_CUDA:bool=true
7. sudo make && make install
8. Add "export PYTHONPATH=$PYTHONPATH:/usr/local/lib/python3.6/pyrealsense2/" to the /etc/profile
9. source /etc/profile







Reference List:
https://github.com/IntelRealSense/librealsense/issues/6964#issuecomment-672059669
https://github.com/IntelRealSense/librealsense/issues/6964#issuecomment-672059669
https://stackoverflow.com/questions/16248775/cmake-not-able-to-find-openssl-library
https://github.com/IntelRealSense/librealsense/tree/master/wrappers/python#building-from-source
