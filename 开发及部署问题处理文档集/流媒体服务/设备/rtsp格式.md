## 一、**海康IPC、NVR取流RTSP**
### 1.1、**老版本**
    rtsp://username:password@<ipaddress>/<videotype>/ch<number>/<streamtype>
    e.g: rtsp://admin:12345@172.6.22.106:554/h264/ch33/main/av_stream
    e.g: rtsp://admin:12345@172.6.22.106:554/h264/ch33/sub/av_stream
![图片]("./images/hkws_rtsp_url_old.png")
注：老URL，NVR（>=64路的除外）的IP通道从33开始。
### 1.2、**新版本，DS系列**
    rtsp://username:password@<address>:<port>/Streaming/Channels/<id>(?parm1=value1&parm2-=value2…)
    e.g: rtsp://admin:12345@172.6.22.234:554/Streaming/Channels/101
![图片]("./images/hkws_rtsp_url.png")
注：新URL，NVR通道号全部按顺序从1开始。
### 1.3、**回放**
    rtsp://username:password@<address>:<port>/Streaming/tracks/<id>(?parm1=value1&parm2-=value2…)
    e.g: rtsp://admin:12345@172.6.22.106:554/Streaming/tracks/101?starttime=20120802t063812z&endtime=20120802t064816z
![图片]("./images/hkws_rtsp_url_track.png")
表示以单播形式回放指定设备的通道中的录像文件，时间范围是starttime到endtime，其中starttime和endtime的格式要符合ISO 8601。具体格式是YYYYMMDD”T”HHmmSS.fraction”Z”，Y是年，M是月，D是日，T是时间分格符，H是小时，M是分，S是秒，Z是可选的、表示Zulu(GMT) 时间。

注意：很多时候我们用命令行来验证RTSP回放流的时候，一定要将整个RTSP-URL用双引号包括起来，“RTSP-URL”，因为CMD里面&符号是特殊字符，不用双引号包起来，整个地址会被切割分成几个部分。
## 二、**海康流媒体服务取流RTSP**
### 2.1、**流媒体V4.0 iVMS-4200 V2.0配套流媒体服务器**
    rtsp://<流媒体address>:<流媒体port>/Devicehc8://<address>:<port>:0:0?username=username&password=password
    e.g: rtsp://172.6.24.15:554/Devicehc8://172.6.22.106:8000:0:0?username=admin&password=12345
![图片]("./images/hkws_ivms_rtsp_url.png")
### 2.2、**流媒体V2.0**
    rtsp://<流媒体address>:<流媒体port>/<address>:<port>:HIK-DS8000HC:2:0:admin:12345/av_stream
    e.g: rtsp://172.6.24.15:554/172.6.22.106:8000:HIK-DS8000HC:2:0:admin:12345/av_stream
![图片]("./images/hkws_ivms2_rtsp_url.png")
注：流媒体2.0的取流URL不是标准的RTSP协议，必须使用流媒体SDK（客户端）才支持取流的，放在这里只是为了给流媒体4.0做参照的。
## 三、**大华**
### 3.1、**RTSP**
    rtsp://username:password@ip:port/cam/realmonitor?channel=1&subtype=0
    e.g: rtsp://admin:admin@192.168.100.184:554/cam/realmonitor?channel=1&subtype=0
![图片]("./images/dh_rtsp_url.png")
### 3.2、**回放**
    rtsp://username:password@ip:port/cam/playback?channel=1&subtype=0&starttime=2018_12_18_12_05_00&endtime=2018_12_18_12_07_00
    e.g: rtsp://test:admin@192.168.6.183:554/cam/playback?channel=92&subtype=0&starttime=2018_12_18_12_05_00&endtime=2018_12_18_12_07_00
![图片]("./images/dh_rtsp_url_back.png")
# 详情见
[详细页面][1]
[1]: https://www.glowjs.com/docs/nodenvr/device-rtsp