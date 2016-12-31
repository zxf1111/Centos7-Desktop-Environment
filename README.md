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
