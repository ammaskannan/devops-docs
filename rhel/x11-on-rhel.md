# Enabling x11 on RHEL

Follow this steps (for installing xorgx11 apps like xclock, please see the step after that)
<https://aws.amazon.com/blogs/compute/how-to-enable-x11-forwarding-from-red-hat-enterprise-linux-rhel-amazon-linux-suse-linux-ubuntu-server-to-support-gui-based-installations-from-amazon-ec2/>

Download the rpm xorg-x11-apps-7.7-24.fc30.x86_64 from the below site using wget (if wget is not there install it using sudo dnf instlal wget) <https://rpmfind.net/linux/rpm2html/search.php?query=xorg-x11-apps&submit=Search+...&system=&arch=>

 and then install the rpm

`sudo dnf localinstall xorg-x11-apps-7.7-24.fc30.x86_64.rpm`

 then run xclock
`xclock`

xclock should open on your screen

error with chromium -- Couldn't open libGL.so.1: libGL.so.1: cannot open shared object file: No such file or directory
fix in this link and executed as below commands <https://unix.stackexchange.com/questions/348429/missing-libgl-on-fedora-cannot-install-it>

        sudo dnf repository-packages epel list | grep mesa
        dnf repoquery -l libglvnd-glx.x86_64
        sudo dnf repoquery -l libglvnd-glx.x86_64
        sudo dnf install libglvnd-glx.x86_64

Now, if you start chromium browser, it will start and it will open in xming in your machine.
And the robot tests also will run without commenting Open Browser and Maximize Browser commands.
