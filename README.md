this fork tries to make use of canfi on a raspberry pi

using raspbian, currently the steps to build are:

    # das mono im raspbian repo ist steinalt - daher falls schon installiert
    sudo apt purge mono-complete mono-runtime mono-devel
    
    # mono keyserver/repo/...
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
    echo "deb http://download.mono-project.com/repo/debian stable-raspbianstretch main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
    sudo apt update
    
    # falls uns mono-devel nicht reicht dann evtl mono-complete versuchen
    sudo apt install mono-devel # hier musste ich trotz key import unverified bestaetigen [y/N] o.0
    
    # fetch & build
    git clone https://github.com/daef/CANFI.git && cd CANFI
    git checkout canfi-on-rpi
    msbuild
    
    # test dat shieeet
    cd CANFI/bin/Debug
    
    pi@raspberrypi:~/CANFI/CANFI/bin/Debug $ mono --debug CANFI.exe


# CANFI
(C)heap (A)utomatic (N)oise (F)igure (I)ndicator with DVB-T stick
This software demonstrates the use of a DVB-T receiver as cheap noise figure indicator.  
The benefits are:

    Small budget ( < 100€)
    USB powered
    almost compatible to popular industrial devices
    (HP8970, Eaton 2075 and others)
    commercial noise sources can be used
    PC based user interface with many additional functions

Copyright (C) 2015 DL2ALF

Special thanks to DL8AAU and DF9IC for ideas, support and testing.
