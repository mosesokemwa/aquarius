### How do you install Android Studio for Ubuntu 14.04 LTS

Android Studio depends on Java, and Oracle Java 7 or 8 is recommended

    sudo add-apt-repository -y ppa:webupd8team/java

    sudo apt-get update

    sudo apt-get install oracle-java7-installer oracle-java7-set-default

Add the Android Studio PPA

    sudo add-apt-repository ppa:paolorotolo/android-studio

Then update package lists and install it:

    sudo apt-get update

    sudo apt-get install android-studio

Once installed, start the setup wizard from the Unity Dash or just run command

    /<path>/android-studio/bin/studio.sh
    
The first time you run studio.sh do it using the terminal and not by double-clicking. e.g.       

    ./<path>/android-studio/bin/studio.sh

After it opens, you can go to ``Configure-->Create Desktop`` Entry to have a permanent shortcut to the application that you can use from there on.

##### HAPPY CODING