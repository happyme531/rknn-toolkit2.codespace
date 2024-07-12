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
    wget \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# 设置工作目录
WORKDIR /workspace

# 下载并安装RKNN Toolkit 2
RUN wget https://github.com/airockchip/rknn-toolkit2/raw/master/rknn-toolkit2/packages/rknn_toolkit2-2.0.0b0%2B9bab5682-cp311-cp311-linux_x86_64.whl \
    && pip3 install rknn_toolkit2-2.0.0b0+9bab5682-cp311-cp311-linux_x86_64.whl --break-system-packages \
    && rm rknn_toolkit2-2.0.0b0+9bab5682-cp311-cp311-linux_x86_64.whl

# 安装最新版PyTorch
RUN pip3 install --upgrade torch torchvision torchaudio jupyter --break-system-packages

# 克隆RKNN模型仓库
RUN git clone https://github.com/airockchip/rknn_model_zoo.git

# 清理缓存
RUN pip3 cache purge

# 设置默认命令
CMD ["/bin/bash"]
