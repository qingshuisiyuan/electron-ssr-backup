# 收集已知问题和解决方案

### 如何查看软件错误信息：
终端输入electron-ssr运行（再此之前请手动退出已经打开的ssr软件或者其他代理软件、工具，包括浏览器的代理插件等）<br>
注意：提交issues的时候请把报错信息中的个人信息（ip，密码等）删除。<br>
日志位置：Linux：/home/UserName/.config/electron-ssr/logs/shadowsocksr-client.log<br>
其他系统：右键小飞机-帮助-查看日志<br>
注意：提交日志的时候请把报错信息中的个人信息（ip，密码等）删除。<br>
建议两个一起提交。<br>

### Archlinux or Manjaro 无法运行的问题解决
Manjaro/Archlinux 运行程序时无法运行，在终端运行 electron-ssr 发现缺少 lib-gconf.so 这个库文件，只需要安装 gconf 即可解决<br>
- `sudo pacman -S gconf`

###  [error] 2019-08-03 16:26:47 INFO util.py:85 loading libcrypto from libcrypto.so.1.0.0
- `sudo apt-get install libssl-dev`
- `sudo apt-get install libsodium-dev`<br>
以上两条命令是为了解决软件报错提示缺少libcrypto.so这个库，但实际能否解决并未能验证

### [error] 2019-06-11 22:46:25 INFO util.py:85 loading libsodium from libsodium.so.23
- `sudo apt install libsodium libsodium-dev`

### Fedora缺少库导致无法使用 chacha20* 模式
- `sudo dnf install libsodium libsodium-devel`

### Manjaro无法代理（其他linux可以参考）
一、PAC模式不可用
安装proxychains，可从软件仓库安装或github
``` bash
sudo vi /etc/proxychains.conf
```
将socks4 127.0.0.1 9095改为
```bash
socks5 127.0.0.1 1080
```
重启服务

二、全局模式不可用

系统设置-网络-系统代理设置http、https代理为127.0.0.1:12333；socks代理设置为127.0.0.1:1080<br>
以上端口要与electron-ssr的设置一致