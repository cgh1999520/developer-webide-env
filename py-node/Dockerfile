# 基于codercom/code-server:latest镜像构建
FROM codercom/code-server:latest

# 设置容器内的用户为root（对应user: "0:0"以及DOCKER_USER=root的配置）
USER root

# 配置卷挂载，和docker-compose.yml中的volumes配置对应
#VOLUME ["/home/coder/.local", "/home/coder/.config", "/root/code"]

# 设置环境变量，与docker-compose.yml中的environment配置对应
ENV DOCKER_USER=root
SHELL ["/bin/bash", "-c"]

# 执行相关命令，实现安装软件等功能，对应entrypoint里的逻辑
RUN bash <(curl -sSL https://linuxmirrors.cn/main.sh) --source mirrors.aliyun.com
RUN apt-get update 
# 更新包列表并安装必要的依赖  
RUN apt-get update && apt-get install -y \
    curl \
    git \
    build-essential \
    libssl-dev \
    zlib1g-dev \
    libbz2-dev \
    libreadline-dev \
    libsqlite3-dev \
    libffi-dev \
    liblzma-dev \
    && rm -rf /var/lib/apt/lists/*  

# 设置环境变量  
ENV HOME /root  
ENV PYENV_ROOT $HOME/.pyenv  
ENV PATH $PYENV_ROOT/bin:$PATH  

# 安装 pyenv  
RUN curl https://pyenv.run | bash  

# 初始化 pyenv  
RUN echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc && \
    echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc && \
    echo 'eval "$(pyenv init --path)"' >> ~/.bashrc && \
    echo 'eval "$(pyenv init -)"' >> ~/.bashrc && \
    echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc  

# 加载 pyenv（为了在Docker构建时可以使用pyenv）  
RUN bash -c "source ~/.bashrc && pyenv install 3.6 && pyenv global 3.6"  

RUN curl -sL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs

# 确保终端使用pyenv（为了在后续的docker run中能正常使用）  

WORKDIR /home/coder

EXPOSE 8080

ENTRYPOINT ["bash", "-c", "source ~/.bashrc && exec bash", "/usr/bin/entrypoint.sh", "--bind-addr", "0.0.0.0:8080", "."]
