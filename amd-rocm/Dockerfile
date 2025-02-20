FROM rocm/pytorch:latest

ENV ACT_VERSION=0.2.11

RUN apt update &&\
    apt install -y bash wget cmake make gcc


RUN mkdir -p /act &&\
    chmod go+w /act

WORKDIR /act

RUN curl https://dl.gitea.com/act_runner/${ACT_VERSION}/act_runner-${ACT_VERSION}-linux-amd64 --output act_runner

COPY ../scripts/run.sh /act/run.sh

ENTRYPOINT [ "/bin/bash", "/act/run.sh" ]
