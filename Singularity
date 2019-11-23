Bootstrap: docker
From: ubuntu:bionic

%labels
Author "Randall Cab White - rcwhite@stanford.edu"


#########
#%setup
#########

#Downlaod packages
%post
  apt-get -ym update
  apt-get -ym install wget curl gcc gfortran python python3 tar bzip2 make cmake libboost-all-dev libblas-dev liblapacke-dev libatlas-base-dev libopenblas-dev libfftw3-dev libgromacs-dev gromacs-data gromacs
  mkdir -p /build
  cd /build
wget https://github.com/channotation/chap/archive/version_0_9_1.tar.gz
tar zxvf version_0_9_1.tar.gz
#wget ftp://ftp.gromacs.org/pub/gromacs/gromacs-2019.4.tar.gz
#tar zxvf gromacs-2019.4.tar.gz


ln -s /usr/lib/x86_64-linux-gnu /usr/share/lib/x86_64-linux-gnu

cd chap-version_0_9_1*
mkdir build
cd build
cmake ../ -DGROMACS_DIR=/usr/share/gromacs/cmake/gromacs
make
make install

%environment
  export IMAGE_NAME="chap"
%runscript
