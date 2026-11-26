# 鹤视·直播

基于 [lizongying/my-tv-0](https://github.com/lizongying/my-tv-0) 定制的 Android TV IPTV 播放器。

## 说明

- 面向 Android TV / 电视盒子使用，遥控器方向键、OK、返回键可操作。
- 默认视频源切换为公开社区源 `vbskycn/iptv` 的 IPv4 源。
- 默认 EPG 使用公开 XMLTV 源，支持启动后自动更新。
- 本仓库只开源源代码，不包含发布签名密钥、个人 Token、个人收款码或本地构建产物 APK。

## 使用

- 遥控器 OK / 触屏单击：打开频道列表
- 遥控器右键 / 触屏双击：打开设置
- 遥控器左键 / 触屏长按：打开节目单
- 返回键：关闭频道列表 / 设置 / 节目单
- 聚焦频道标题时右键：收藏 / 取消收藏
- 设置页「远程配置」会展示局域网配置地址，可用手机扫码配置视频源

## 构建

环境要求：JDK 21、Android Gradle Plugin 可用的 Android SDK。

如果 Gradle 无法自动找到 Android SDK，请先设置环境变量：

```bash
export JAVA_HOME="/Applications/Android Studio.app/Contents/jbr/Contents/Home"
export ANDROID_HOME="$HOME/Library/Android/sdk"
export ANDROID_SDK_ROOT="$ANDROID_HOME"
```

然后构建：

```bash
./gradlew assembleDebug
```

构建产物默认位于：

```text
app/build/outputs/apk/debug/app-debug.apk
```

## 视频源格式

### txt

```text
组名,#genre#
标题,视频地址
```

### m3u

```text
#EXTM3U x-tvg-url=""
#EXTINF:-1 tvg-id="" tvg-chno="" tvg-name="标准标题" tvg-logo="图标" group-title="组名",标题
#EXTVLCOPT:http-user-agent=
#EXTVLCOPT:http-referrer=
视频地址
```

### json

```json
[
  {
    "group": "组名",
    "name": "标准标题",
    "title": "标题",
    "logo": "图标",
    "number": "频道号",
    "uris": ["视频地址"],
    "headers": {
      "user-agent": ""
    }
  }
]
```

## 安全与隐私

- 仓库不提交 `local.properties`、`.env`、签名证书、Token、账号密码或构建 APK。

## 免责声明

本项目不托管、不生产任何直播流内容。内置与默认视频源均来自公开网络资源，仅用于技术学习和个人研究；第三方源的可用性、合法性、稳定性由使用者自行确认。

## 致谢

- 原项目：[lizongying/my-tv-0](https://github.com/lizongying/my-tv-0)，MIT License
- 频道源参考：[vbskycn/iptv](https://github.com/vbskycn/iptv)
- EPG 参考：[fanmingming/live](https://github.com/fanmingming/live)、`epg.112114.xyz`

作者：Enzo · [博客](https://blog.enzocreative.me)。
