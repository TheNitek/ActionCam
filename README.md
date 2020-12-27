# ActionCam
Trying to reverse engineer action cams base on the HiMobileCam SDK (like the Dragon Touch Vista 5)


## HTTP API
When connected via WiFi the cam is listening to port 80 on IP 192.168.0.1
Return codes seem to be -5555 if parameters are missing and -2222 if values are unknown

* http://192.168.0.1/ Browseable file system provided by a [thttpd](https://acme.com/software/thttpd/) (file system path is /app/bin/)
* http://192.168.0.1/cgi-bin/hisnet/ty.cgi
* * No params
* http://192.168.0.1/cgi-bin/hisnet/client.cgi
* http://192.168.0.1/cgi-bin/hisnet/getworkstate.cgi
* * No params
* http://192.168.0.1/cgi-bin/hisnet/getworkmode.cgi
* * No params
* http://192.168.0.1/cgi-bin/hisnet/workmodecmd.cgi
* * e.g http://192.168.0.1/cgi-bin/hisnet/workmodecmd.cgi?-cmd=start
* * -cmd START, STOP
* http://192.168.0.1/cgi-bin/hisnet/setworkmodeparam.cgi
* * e.g. http://192.168.0.1/cgi-bin/hisnet/setworkmodeparam.cgi?&-workmode=SLOW_REC&-type=MEDIAMODE&-value=720P120fps
* * -workmode
* * -type
* * -value
* http://192.168.0.1/cgi-bin/hisnet/getworkmodeparam.cgi
* * 'http://192.168.0.1/cgi-bin/hisnet/getworkmodeparam.cgi?&-workmode=SLOW_REC&-type=MEDIAMODE
* * -workmode
* * -type
* http://192.168.0.1/cgi-bin/hisnet/setcommparam.cgi
* * -type (see getcommparamcapability.cgi) 
* * -value
* http://192.168.0.1/cgi-bin/hisnet/getcommparam.cgi
* * -type (see getcommparamcapability.cgi) 
* http://192.168.0.1/cgi-bin/hisnet/getworkmodeparamcapability.cgi
* * e.g. http://192.168.0.1/cgi-bin/hisnet/getworkmodeparamcapability.cgi?-workmode=SLOW_REC&-type=MEDIAMODE
* * -workmode = NORM_REC, LOOP_REC, LPSE_REC, SLOW_REC, SING_PHOTO, DLAY_PHOTO, LPSE_PHOTO, BURST, RECSNAP, PLAYBACK, UPGRADE, USB_STORAGE, SUSPEND, HDMI_PREVIEW, HDMI_PLAYBACK
* * -type = MEDIAMODE, PHOTO_SCENE, PHOTO_OUTPUT_FMT, DELAY_TIME, LAPSE_INTERVAL, BURST_TYPE, LOOP_TYPE, ENC_PAYLOAD_TYPE, PROTUNE_EXP_EV, PROTUNE_EXP_TIME, PROTUNE_ISO, PROTUNE_WB, PROTUNE_D, DISTRY, TIME, FLAME
* http://192.168.0.1/cgi-bin/hisnet/getcommparamcapability.cgi
* * e.g. http://192.168.0.1/cgi-bin/hisnet/getcommparamcapability.cgi?-type=POWERON_ACTION
* * -value POWERON_ACTION, FOV, DATE_FORMAT, ANTI_FLICKER, SYS_DORMANT, SCREEN_DORMANT, LANGUAGE, VIDEO_FORMS (might be missing some!)
* http://192.168.0.1/cgi-bin/hisnet/checkupgradepktinfo.cgi
* http://192.168.0.1/cgi-bin/hisnet/getvideoverbosefileinfo.cgi
* * e.g. http://192.168.0.1/cgi-bin/hisnet/getvideoverbosefileinfo.cgi?-name=sd/DCIM/100HSCAM/NORM0005.MP4
* * -name
* http://192.168.0.1/cgi-bin/hisnet/sendclickkey.cgi
* http://192.168.0.1/cgi-bin/hisnet/setloglevel.cgi
* http://192.168.0.1/cgi-bin/hisnet/getdeviceattr.cgi
* * no params
* http://192.168.0.1/cgi-bin/hisnet/getsdstatus.cgi
* * no params
* http://192.168.0.1/cgi-bin/hisnet/getsystime.cgi
* * no params
* http://192.168.0.1/cgi-bin/hisnet/setsystime.cgi
* http://192.168.0.1/cgi-bin/hisnet/reset.cgi (danger!, deletes all custom settings!)
* * no params
* http://192.168.0.1/cgi-bin/hisnet/sdcommand.cgi
* http://192.168.0.1/cgi-bin/hisnet/getbatterycapacity.cgi
* * no params
* http://192.168.0.1/cgi-bin/hisnet/setwifi.cgi
* * enablewifi
* * wifissid
* * wifikey
* * secretmode
* * wifichannel
* * links
* http://192.168.0.1/cgi-bin/hisnet/getwifi.cgi
* * no params
* http://192.168.0.1/cgi-bin/hisnet/getfilecount.cgi
* * no params
* http://192.168.0.1/cgi-bin/hisnet/getfilelist.cgi
* * Random parameters (without leading "-") seem to do something?!
* http://192.168.0.1/cgi-bin/hisnet/getfileinfo.cgi
* * e.g. http://192.168.0.1/cgi-bin/hisnet/getfileinfo.cgi?-name=sd/DCIM/100HSCAM/SING0001.JPG
* * -name
* http://192.168.0.1/cgi-bin/hisnet/deletefile.cgi
* * -name
* http://192.168.0.1/cgi-bin/hisnet/deleteallfiles.cgi (danger!, deletes all recordings)
* * No params

## Video Stream
* rtsp://192.168.0.1:554/livestream/11
* rtsp://192.168.0.1:554/livestream/12

## Docs
* https://www.showdoc.com.cn/page/3464949758673814
* https://www.showdoc.com.cn/page/3464913110566109
* https://www.showdoc.com.cn/page/3529336024967348
