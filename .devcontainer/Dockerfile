FROM gcc:9.5
WORKDIR /

RUN wget https://github.com/intel/tbb/archive/v2020.0.tar.gz
RUN tar zxvf v2020.0.tar.gz
RUN rm v2020.0.tar.gz

WORKDIR /oneTBB-2020.0
RUN make compiler=gcc stdver=c++17

RUN mkdir /usr/local/oneTBB-2020.0
RUN cp -r include /usr/local/oneTBB-2020.0/include
RUN ln -s /usr/local/oneTBB-2020.0/include/tbb /usr/local/include/tbb

RUN cp -r build/*_release /usr/local/oneTBB-2020.0/lib
RUN ln -s /usr/local/oneTBB-2020.0/lib/libtbb.so.2 /usr/local/lib/libtbb.so
RUN ln -s /usr/local/oneTBB-2020.0/lib/libtbbmalloc.so.2 /usr/local/lib/libtbbmalloc.so
RUN ln -s /usr/local/oneTBB-2020.0/lib/libtbbmalloc_proxy.so.2 /usr/local/lib/libtbbmalloc_proxy.so

RUN apt-get update && apt-get install -y \
    vim \
    nano

RUN apt-get install zsh -y
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" -y
RUN echo 'export LD_LIBRARY_PATH=/usr/local/oneTBB-2020.0/lib:$LD_LIBRARY_PATH' >> ~/.zshrc
COPY git-setup.sh /tmp/
RUN cat /tmp/git-setup.sh >> ~/.zshrc
RUN chsh -s $(which zsh)