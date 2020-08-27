FROM mrcide/naomi-base:latest

COPY docker/bin /usr/local/bin/

RUN install_packages --repo=https://mrc-ide.github.io/drat \
        mockery \
        covr \
        ssh

RUN install_remote \
        mrc-ide/naomi

COPY . /src
RUN cd /src/hintr && ./scripts/build_test_data
RUN R CMD INSTALL /src/hintr

RUN install_remote \
        mrc-ide/hintr2

RUN R CMD INSTALL /src

WORKDIR /src
RUN R CMD build .
ENTRYPOINT ["/bin/bash"]
