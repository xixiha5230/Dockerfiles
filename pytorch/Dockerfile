FROM pytorch/pytorch:1.11.0-cuda11.3-cudnn8-runtime

# 清华源
RUN echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse" > /etc/apt/sources.list
RUN echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse" >> /etc/apt/sources.list
RUN echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse" >> /etc/apt/sources.list
RUN echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse" >> /etc/apt/sources.list

# root密码xixiha
RUN echo 'root:xixiha' | chpasswd

# 安装ssh
RUN apt update
RUN apt install openssh-server -y
RUN /usr/bin/ssh-keygen -A
RUN echo "PermitRootLogin yes" >> /etc/ssh/sshd_config
RUN echo "PasswordAuthentication yes" >> /etc/ssh/sshd_config
RUN service ssh restart
EXPOSE 22

# 开启conda环境
RUN echo "source /opt/conda/bin/activate" >> ~/.bashrc 
RUN echo "conda activate base" >> ~/.bashrc

# 开启显示
RUN echo "export DISPLAY=unix:0" >> ~/.bashrc

# 安装git
RUN apt install git -y
RUN git config --global user.name xixiha
RUN git config --global user.email xixiha5230@gmail.com

# 安装opencv
RUN apt install ffmpeg libsm6 libxext6  -y

# 安装python包
COPY requirements.txt /root/requirements.txt
RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
RUN pip install -r /root/requirements.txt

# 复制vscode
COPY .vscode-server /root/.vscode-server

ENTRYPOINT ["/usr/sbin/sshd","-D"]
# ENTRYPOINT ["/bin/bash"]
