BootStrap: docker
From: ubuntu:18.04

%labels
    Maintainer zyou@osc.edu

%help

    Container with following molecular graphics systems for Ubuntu 18.04
    - OpenChemistry 1.93.0
    - Gabedit 2.4.8
    - Jmol 14.6.4

%environment
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/openchemistry/lib
    export PATH=$PATH:/usr/local/openchemistry/bin

%post
    export LC_ALL=C
    apt update
    apt upgrade -y
    DEBIAN_FRONTEND=noninteractive apt install -y \
        build-essential git cmake qtbase5-dev libxml2-dev python

    # Gabedit & Jmol
    DEBIAN_FRONTEND=noninteractive apt install -y gabedit
    DEBIAN_FRONTEND=noninteractive apt install -y jmol

    # OpenChemistry
    OSC_BUILD=/osc_build
    mkdir -p $OSC_BUILD
    cd $OSC_BUILD
    git clone --recursive git://github.com/OpenChemistry/openchemistry.git
    cd openchemistry
    git checkout 1.93.0
    git submodule update --init
    cd avogadrogenerators
    git checkout master

    cd $OSC_BUILD
    mkdir -p build && cd build
    cmake ../openchemistry
    cmake --build . --config Release
    mv prefix /usr/local/openchemistry 
    test -d $OSC_BUILD && rm -rf $OSC_BUILD

    # Clean up
    apt autoclean
    apt autoremove --purge -y
    rm -rf /var/lib/apt/lists/*
