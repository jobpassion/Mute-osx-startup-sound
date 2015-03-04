## 一共两个脚本
- 开机脚本：
`
    MUTED=$(cat /usr/local/etc/init.d/volume_muted)
    #/usr/bin/osascript -e "set volume output volume $VOLUME"
    /usr/bin/osascript -e "set volume output muted $MUTED"

`
