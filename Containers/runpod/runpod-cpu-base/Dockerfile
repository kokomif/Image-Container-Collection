ARG BASE_IMAGE=runpod/base:0.6.2-cpu

FROM ${BASE_IMAGE} as dev-base

SHELL ["/bin/bash", "-o", "pipefail", "-c"]
ENV DEBIAN_FRONTEND noninteractive\
    SHELL=/bin/bash
RUN apt-get update --yes && \
    # - apt-get upgrade is run to patch known vulnerabilities in apt-get packages as
    #   the ubuntu base image is rebuilt too seldom sometimes (less than once a month)
    apt-get upgrade --yes && \
    apt install --yes --no-install-recommends\
    wget\
    bash\
    curl\
    git\
    aria2\
    openssh-server &&\
    apt-get clean && rm -rf /var/lib/apt/lists/* && \
    echo "en_US.UTF-8 UTF-8" > /etc/locale.gen
RUN pip install jupyterlab ipywidgets jupyter-archive

RUN mkdir workspace

#For Local RUN ADD start.sh .

ADD ./Containers/runpod/runpod-cpu-base/start.sh .

RUN chmod +x start.sh

CMD [ "./start.sh" ]

