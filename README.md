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
* source py3env/bin/activate
* pip install package-name

###my prompt
* PS1='\[\e]0;\w\a\]\n\[\e[32m\]\u@\h $(date +%F*%T) \[\e[33m\]\w\[\e[0m\]\n\$ '

### my terminator 4 windows
** edit ~/.config/terminator/config 
    
    [layouts]
  
    [[default]]
    
    [[[root]]]
      position = -4:0
      type = Window
      order = 0 
      parent = ""
      size = 1072, 1884

    [[[grand]]]
      position = 536 
      type = HPaned
      order = 0 
      parent = root
    [[[left]]]
      position = 942 
      type = VPaned
      order = 0 
      parent = grand
    [[[right]]]
      position = 942 
      type = VPaned
      order = 1 
      parent = grand



    [[[terminal1]]]
      profile = default
      type = Terminal
      order = 0 
      parent = left
      command = "cd ~/code/foo; bash"
    [[[terminal2]]]
      profile = default
      type = Terminal
      order = 1 
      parent = left
      command = "cd ~/bar/baz; bash"



    [[[terminal3]]]
      profile = default
      type = Terminal
      order = 1 
      parent = right
      command = ""
    [[[terminal4]]]
      profile = default
      type = Terminal
      order = 0 
      parent = right
      command = "cmus; bash"
###don't save history before space 
   * export HISTCONTROL=ignorespace
