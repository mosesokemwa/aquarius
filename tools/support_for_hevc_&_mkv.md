**If vlc shows following error**

    "No suitable decoder module VLC does not support the audio or video format hevc. Unfortunately there is no way for you to fix this."

**Then try to install libde265 via PPA.**

    sudo apt-add-repository ppa:strukturag/libde265

    sudo apt-get update

    sudo apt-get install vlc-plugin-libde265

**VLC should now play these media files after installation has been completed successfully.**