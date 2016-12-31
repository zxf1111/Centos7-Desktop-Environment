# Centos7-Desktop-Environment

**1st yum groupinstall X11**

###GNOME Desktop Environmen
   
* yum -y groups install "GNOME Desktop" 
*  echo "exec gnome-session" >> ~/.xinitrc
* startx 

###KDE-Desktop
* yum -y groups install "KDE Plasma Workspaces" 
* echo "exec startkde" >> ~/.xinitrc
* startx
  
###Xfce Desktop Environment
  
* yum --enablerepo=epel -y groups install "Xfce" 
* echo "exec /usr/bin/xfce4-session" >> ~/.xinitrc 
* startx

###set default startx 
* on centos6 vim /etc/inittab
* change the number in the line id:3:initdefault: from a 3 to a 5
* on centos7 
* systemctl get-default  multi-user.target: analogous to runlevel 3 /etc/inittab
* systemctl set-default graphical.target

###change en33 to old eth0
* vi /etc/default/grub  At the end of GRUB_CMDLINE_LINUX line append "net.ifnames=0 biosdevname=0"
* grub2-mkconfig -o /boot/grub2/grub.cfg
* reboot

###install python35
* yum install -y python35u python35u-libs python35u-devel python35u-pip
* which -a python3.5
* /bin/python3.5
* /usr/bin/python3.5

###python35 virtualenv
* virtualenv -p /usr/bin/python3 py3env
*source py3env/bin/activate
*pip install package-name
