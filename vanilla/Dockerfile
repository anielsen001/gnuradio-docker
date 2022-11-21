FROM ubuntu:20.04
LABEL  maintainer="Aaron Nielsen - apn@apnielsen.com"

RUN apt-get update

# else it will output an error about Gtk namespace not found
RUN apt-get install -y gir1.2-gtk-3.0

# X11 needs to be installed
RUN apt-get install -y libx11-dev

# to have add-apt-repository available
RUN apt-get install -y software-properties-common

# add gnu-radio apt repository
RUN add-apt-repository ppa:gnuradio/gnuradio-releases

# update apt database after adding gnuradio ppa
RUN apt-get update

# create user gnuradio with sudo (and password gnuradio)
RUN apt-get install -y sudo
RUN useradd --create-home --shell /bin/bash -G sudo gnuradio
RUN echo 'gnuradio:gnuradio' | chpasswd

# install gnuradio
RUN apt install -y gnuradio

# installing other packages needed for downloading and installing OOT modules
RUN apt-get install -y gnuradio-dev cmake git libboost-all-dev libcppunit-dev liblog4cpp5-dev python3-pygccxml pybind11-dev liborc-dev python3-pip

# Fix dependency issue as noted on 'InstallingGR' wiki page for 3.10
RUN pip install packaging

USER gnuradio

WORKDIR /home/gnuradio

ENV PYTHONPATH "${PYTHONPATH}:/usr/local/lib/python3/dist-packages"

CMD bash