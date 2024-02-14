# PlexMusicScanner-Mod

代码 摘抄自[韩风大佬的b站视频](https://www.bilibili.com/video/BV1qr4y1S7KL/?vd_source=c4ce73eabed370236ad7d8ab6079980c)
由于Plex Media Server的代理脚本是用Python 2写的，我不熟悉这种版本的Python，**脚本没有详细的测试，介意请勿使用!!!**

另外，音乐标签的读取依赖mutagen库，这个库5年前就放弃了对Python2的支持，我找到最后一版支持Python2的版本[7ed00ef](https://github.com/quodlibet/mutagen/blob/7ed00ef44614555d917d42bcd597d32040e40dab)，并粗暴地替换了官方PMS内置的mutagen库。

如果你发现了本项目出现了bug，且想自己在韩风大佬基础上修改，可以使用meld工具对比韩风大佬的改动，然后在你自己PMS的Scanner.bundle、LocalMedia.bundle上修改。

## Features

在官方基础上，该插件音乐格式的刮削支持：
* `aac`
* `wav`
* `ape`
* `dsf`

前三项是韩风大佬添加的，dsf是我参照韩风大佬代码添加的。

## Usage
1. 下载本项目的LocalMedia.bundle、Scanners.bundle文件夹。
2. 找到资源库的位置，
    * MacOS: /Applications/Plex Media Server.app/Contents/Resources
    * Linux: /usr/lib/plexmediaserver/Resources
3. 进入Plug-ins-xxxx（这个xxxx是和版本号的hash对应)，备份LocalMedia.bundle、Scanners.bundle文件夹。
```bash
sudo mv LocalMedia.bundle LocalMedia.bundle_bak
sudo mv Scanners.bundle Scanners.bundle_bak
```
4. 将下载的LocalMedia.bundle、Scanners.bundle文件夹放到资源库的Plug-ins-xxx文件夹下：
```bash
# 注意修改权限，否则会出现代理不再后台显示
sudo chmod -R 755 LocalMedia.bundle Scanners.bundle
# 如果/lib/systemd/system/plexmediaserver.service中的User=plex，那么执行：
sudo chown -R plex:plex LocalMedia.bundle Scanners.bundle
# 如果/lib/systemd/system/plexmediaserver.service中的User=root，那么执行：
sudo chown -R root:root LocalMedia.bundle Scanners.bundle
```
5. [可选] 去下载timmy0209的[网易云音乐插件](https://github.com/timmy0209/WangYiYun.bundle)，参考[配套教程](https://zhuanlan.zhihu.com/p/218120206)并安装。
6. 重启Plex Media Server。
7. 然后去后台将音乐媒体库的扫描器更换为Plex Music Scanner(MOD)（推荐重新建立音乐媒体库，避免玄学的缓存导致不更新的问题）