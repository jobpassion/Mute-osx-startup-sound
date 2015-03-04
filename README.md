### 准备两个脚本
- 开机脚本：

==
    #!/bin/sh
    MUTED=$(cat /usr/local/etc/init.d/volume_muted)
    /usr/bin/osascript -e "set volume output muted $MUTED"

==
- 关机脚本：

==
    #!/bin/sh
    /usr/bin/osascript -e 'output muted of (get volume settings)'>/usr/local/etc/init.d/volume_muted
    /usr/bin/osascript -e "set volume output muted true"

==

这两个脚本里都写到了`/usr/local/etc/init.d/volume_muted`，可以自行更改 是关机前把当前音量是否静音的状态写到了文件里，开机脚本读取这里的文件

###接下来添加hook给系统，触发开机执行和关机执行

==
    #打开Terminal执行
    sudo defaults write com.apple.loginwindow LoginHook /path/to/script1
    sudo defaults write com.apple.loginwindow LogoutHook /path/to/script2
==

注意这里两个脚本的路径与事先准备的两个脚本存放路径一致

over
