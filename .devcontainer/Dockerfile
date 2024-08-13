# 基于Debian Bookworm
FROM debian:bookworm

# 设置非交互式环境变量
ENV DEBIAN_FRONTEND=noninteractive

# 安装所需软件
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    git \
    gcc \
    clangd \
    adb \
    gcc-aarch64-linux-gnu \
    g++-aarch64-linux-gnu \
    wget \
    bear \
    cmake \
    python-is-python3 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# 设置工作目录
WORKDIR /workspaces

# 下载并安装RKNN Toolkit 2
RUN wget https://github.com/airockchip/rknn-toolkit2/raw/master/rknn-toolkit2/packages/rknn_toolkit2-2.1.0+708089d1-cp311-cp311-linux_x86_64.whl \
    && pip3 install rknn_toolkit2-2.1.0+708089d1-cp311-cp311-linux_x86_64.whl --break-system-packages \
    && rm rknn_toolkit2-2.1.0+708089d1-cp311-cp311-linux_x86_64.whl

# 安装最新版PyTorch
# RUN pip3 install --upgrade torch torchvision torchaudio --break-system-packages

# Jupyter notebook!
RUN pip3 install --upgrade jupyter --break-system-packages

RUN pip3 install "numpy<2" --break-system-packages

# 清理缓存
RUN pip3 cache purge

# 设置默认命令
CMD ["/bin/bash"]
