# PlexMusicScanner-Mod

代码修改摘抄自[韩风大佬的b站视频](https://www.bilibili.com/video/BV1qr4y1S7KL/?vd_source=c4ce73eabed370236ad7d8ab6079980c)
由于Plex Media Server的代理脚本是用Python 2写的，我不熟悉这种版本的Python，脚本没有详细的测试，介意请勿使用。

## Features

添加了一下音乐格式的刮削：
* `wav`
* `dsf`
* `ape`

## Usage
1. 下载本项目的LocalMedia.bundle_xxx、Scanners.bundle_xxx文件夹。
2. 找到资源库的位置，
    * MacOS: /Applications/Plex Media Server.app/Contents/Resources
    * Linux: /usr/lib/plexmediaserver/Resources
3. 进入Plug-ins-xxxx（这个xxxx是和版本号的hash对应)，备份LocalMedia.bundle、Scanners.bundle文件夹。
```bash
sudo mv LocalMedia.bundle LocalMedia.bundle_bak
sudo mv Scanners.bundle Scanners.bundle_bak
```
4. 将下载的LocalMedia.bundle_xxx、Scanners.bundle_xxx文件夹放到资源库的Plug-ins-xxx文件夹下，并去掉xxxx：
```bash
sudo mv LocalMedia.bundle_xxx LocalMedia.bundle
sudo mv Scanners.bundle_xxx Scanners.bundle
# 注意修改权限，否则会出现代理不再后台显示
sudo chmod -R 755 LocalMedia.bundle Scanners.bundle
sudo chown -R root:root LocalMedia.bundle Scanners.bundle
```
5. [可选] 去下载timmy0209的[网易云音乐插件](https://github.com/timmy0209/WangYiYun.bundle)，参考[配套教程](https://zhuanlan.zhihu.com/p/218120206)并安装。
6. 重启Plex Media Server。
7. 然后去后台将音乐媒体库的扫描器更换为Plex Music Scanner(MOD)

