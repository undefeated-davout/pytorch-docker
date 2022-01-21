FROM pytorch/pytorch:1.10.0-cuda11.3-cudnn8-devel

ENV DEBIAN_FRONTEND=noninteractive
ARG PYTHON_VERSION="3.9.6"

RUN apt-get update && apt-get install -y --no-install-recommends \
        git \
        locales \
        wget \
        unzip && \
    rm -rf /var/lib/apt/lists/*

# 日本語設定
RUN locale-gen ja_JP.UTF-8 && echo "export LANG=ja_JP.UTF-8" >> ~/.bashrc

# pip
RUN pip install -U pip && pip install \
     opencv-python \
     matplotlib \
     jupyter

# Jupyter Notebook設定
ENV CONFIG /root/.jupyter/jupyter_notebook_config.py
ENV CONFIG_IPYTHON /root/.ipython/profile_default/ipython_config.py
RUN jupyter notebook --generate-config --allow-root && \
    ipython profile create
RUN echo "c.NotebookApp.ip = '0.0.0.0'" >>${CONFIG} && \
    echo "c.NotebookApp.port = 8888" >>${CONFIG} && \
    echo "c.NotebookApp.open_browser = False" >>${CONFIG} && \
    echo "c.NotebookApp.iopub_data_rate_limit=10000000000" >>${CONFIG} && \
    echo "c.MultiKernelManager.default_kernel_name = 'python3'" >>${CONFIG} && \
    echo "c.InteractiveShellApp.exec_lines = ['%matplotlib inline']" >>${CONFIG_IPYTHON}

WORKDIR /workspace
RUN chmod -R a+w .

CMD ["jupyter","notebook", "--allow-root"]
