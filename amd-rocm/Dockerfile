FROM rocm/pytorch:latest

ENV ACT_VERSION=0.2.11

RUN apt update &&\
    apt install -y bash wget cmake make gcc


RUN mkdir -p /act &&\
    chmod go+w /act

RUN mkdir /temp

WORKDIR /temp

RUN curl https://dl.gitea.com/act_runner/${ACT_VERSION}/act_runner-${ACT_VERSION}-linux-amd64 --output act_runner

RUN mv act_runner /usr/local/bin/act_runner &&\
    chmod +x /usr/local/bin/act_runner

WORKDIR /

RUN rm -rf /temp

COPY ../scripts/run.sh /usr/local/bin/run.sh

ENTRYPOINT [ "/bin/bash", "/usr/local/bin/run.sh" ]
