# ARG PYTORCH="1.9.0"
# ARG CUDA="11.1"
# ARG CUDNN="8"


# FROM pytorch/pytorch:${PYTORCH}-cuda${CUDA}-cudnn${CUDNN}-devel


# ENV TORCH_CUDA_ARCH_LIST="6.0 6.1 7.0+PTX"
# ENV TORCH_NVCC_FLAGS="-Xfatbin -compress-all"
# ENV CMAKE_PREFIX_PATH="$(dirname $(which conda))/../"


# # To fix GPG key error when running apt-get update

# RUN apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/3bf863cc.pub
# RUN apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1804/x86_64/7fa2af80.pub
# RUN apt-get update && apt-get install -y git ninja-build libglib2.0-0 libsm6 libxrender-dev libxext6 ffmpeg \
#     && apt-get clean \
#     && rm -rf /var/lib/apt/lists/*

# # Install xtcocotools
# RUN pip install cython
# RUN pip install xtcocotools

# # Install MMCV

# RUN pip install --no-cache-dir --upgrade pip wheel setuptools
# RUN pip install mmcv-full==1.6.0

# # Install MMDET
# RUN pip install mmdet==2.25.0



# # Install MMPOSE
# RUN conda clean --all
# RUN git clone https://github.com/open-mmlab/mmpose.git /mmpose
# WORKDIR /mmpose
# RUN mkdir -p /mmpose/data
# ENV FORCE_CUDA="0"
# RUN pip install -r requirements/build.txt
# RUN pip install --no-cache-dir -e .

ARG PYTORCH="1.9.0"
ARG CUDA="11.1"
ARG CUDNN="8"


FROM pytorch/pytorch:${PYTORCH}-cuda${CUDA}-cudnn${CUDNN}-devel


ENV TORCH_CUDA_ARCH_LIST="6.0 6.1 7.0+PTX"
ENV TORCH_NVCC_FLAGS="-Xfatbin -compress-all"
ENV CMAKE_PREFIX_PATH="$(dirname $(which conda))/../"


# To fix GPG key error when running apt-get update

RUN apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/3bf863cc.pub
RUN apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1804/x86_64/7fa2af80.pub
RUN apt-get update && apt-get install -y git ninja-build libglib2.0-0 libsm6 libxrender-dev libxext6 ffmpeg \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install xtcocotools
RUN pip install cython
RUN pip install xtcocotools

# Install MMCV

RUN pip install --no-cache-dir --upgrade pip wheel setuptools
RUN pip install -U openmim
RUN mim install mmcv-full==1.6.0

# Install MMDET
RUN mim install mmdet==2.25.0
RUN mim install mmpose==0.29.0 

# Install MMPOSE
RUN conda clean --all
RUN git clone https://github.com/Per-Ardua-Ad-Astra/yolov7_hrnet /yolov7_hrnet
WORKDIR /mmpose_yolov7
RUN mkdir -p /yolov7_hrnet/data
ENV FORCE_CUDA="0"
RUN pip install -r requirements/build.txt
RUN pip install --no-cache-dir -e .