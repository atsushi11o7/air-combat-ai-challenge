FROM nvidia/cuda:12.6.2-cudnn-devel-ubuntu24.04

# ロケールを設定（UTF-8対応）
ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US:en
ENV LC_ALL=en_US.UTF-8

WORKDIR /workspace

RUN apt-get update && apt-get install -y \
    python3 python3-pip python3-venv python3-dev \
    locales \
    git curl vim unzip \
 && locale-gen en_US.UTF-8 \
 && update-locale LANG=en_US.UTF-8 \
 && rm -rf /var/lib/apt/lists/*

RUN python3 -m venv /opt/venv

RUN /opt/venv/bin/pip install --upgrade pip && \
    /opt/venv/bin/pip install torch==2.7.1+cu126 --index-url https://download.pytorch.org/whl/cu126 && \
    /opt/venv/bin/pip install \
        numpy \
        pandas \
        matplotlib \
        scikit-learn \
        jupyterlab \
        seaborn \
        tqdm \
        ipywidgets \
        ipykernel

RUN /opt/venv/bin/python -m ipykernel install --name air-combat-ai-challenge-dev --display-name "Python (air-combat-ai-challenge-dev)" --sys-prefix

RUN echo "source /opt/venv/bin/activate" >> /root/.bashrc

CMD ["bash"]
