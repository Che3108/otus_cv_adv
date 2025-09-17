FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive TZ="Asia/Krasnoyarsk"

WORKDIR /work_dir
COPY . .
RUN apt-get -y update &&\
    apt-get -y upgrade &&\
    apt-get -y install python3 &&\
    apt-get -y install python3-pip &&\
    apt-get -y install wget &&\
    apt-get -y install ffmpeg &&\
    apt-get -y install unzip &&\
    #wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-keyring_1.1-1_all.deb &&\
    #dpkg -i cuda-keyring_1.1-1_all.deb &&\
    #apt-get update &&\
    #apt-get -y install cuda-toolkit-13-0 &&\
    python3 -m pip install -r requirements.txt --break-system-packages &&\ 
    python3 -m pip install torch torchvision --index-url https://download.pytorch.org/whl/cu129 --break-system-packages

CMD  ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--notebook-dir=/work_dir/notebooks", "--no-browser", "--allow-root"]