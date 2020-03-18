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
  apt-get -ym install wget curl gcc gfortran python python-pip python3 python3-pip tar bzip2 make cmake libboost-all-dev libblas-dev liblapacke-dev libatlas-base-dev libopenblas-dev libfftw3-dev libgromacs-dev gromacs-data gromacs
  mkdir -p /build
  cd /build
wget https://github.com/channotation/chap/archive/version_0_9_1.tar.gz
tar zxvf version_0_9_1.tar.gz
#wget ftp://ftp.gromacs.org/pub/gromacs/gromacs-2019.4.tar.gz
#tar zxvf gromacs-2019.4.tar.gz


mkdir -p /usr/share/lib/

ln -s /usr/lib/x86_64-linux-gnu /usr/share/lib/x86_64-linux-gnu

cd chap-version_0_9_1*
mkdir build
cd build
cmake ../ -DGROMACS_DIR=/usr/share/gromacs/cmake/gromacs
make
make install

#doing pip stuff:

pip install numpy matplotlib pandas
pip3 install numpy matplotlib pandas

%environment
  export IMAGE_NAME="chap"
  export PATH=/usr/local/chap/bin:$PATH
%runscript
