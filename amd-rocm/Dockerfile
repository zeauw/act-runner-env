FROM ubuntu:24.04

ENV ACT_VERSION=0.2.11

RUN apt update &&\
    apt install -y bash wget &&\
    wget https://repo.radeon.com/amdgpu-install/6.2/ubuntu/noble/amdgpu-install_6.2.60200-1_all.deb &&\
    apt install -y ./amdgpu-install_6.2.60200-1_all.deb

# install rocm
RUN amdgpu-install --usecase=rocm

# install envs
RUN apt install -y python3-pip gcc make cmake clang


RUN mkdir -p /act &&\
    chmod go+w /act

WORKDIR /act

RUN curl https://dl.gitea.com/act_runner/${ACT_VERSION}/act_runner-${ACT_VERSION}-linux-amd64 --output act_runner

COPY ../scripts/run.sh /act/run.sh

ENTRYPOINT [ "/bin/bash", "-c", "/act/run.sh" ]
