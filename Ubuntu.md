# Debian系列——Ubuntu18.04为例

## 安装依赖

`sudo apt install libcanberra-gtk-module libcanberra-gtk3-module gconf2 gconf-service libappindicator1`

可选依赖：
- `sudo apt-get install libssl-dev`
- `sudo apt-get install libsodium-dev`
如果软件报错，请安装可选依赖

### 安装软件

`sudo dpkg -i  *.deb`

### 尝试运行软件

终端输入

`electron-ssr`

1.系统需要安装Python2.7，一般系统自带，我是最简化安装没有Python环境，软件运行报错。安装Python之后解决

`sudo apt install python`

看有没有什么报错，如果没有，就在软件里面设置订阅地址看能否更新。<br>
因为终端信息会泄露我的IP，密码，在这里我就不放内容。<br>
请确保没有报错并可以成功更新节点<br>

> *手动退出软件重启系统（笑，Windows习惯）*

**注意：如果到这里你可以使用软件正常的代理就无需进行下一步!!!**

### 系统设置

完成上一步之后并不能实现代理
在启动器中找到系统设置-网络设置-网络代理设置为如下图所示

![](https://github.com/qingshuisiyuan/electron-ssr-backup/blob/master/img/ubuntu/2.png?raw=true)

上诉设置需要与软件中的设置一样（端口）

### 开始上网
选择节点-选择上网模式
到这里我已经可以pac上网或全局上网

![](https://github.com/qingshuisiyuan/electron-ssr-backup/blob/master/img/ubuntu/3.png?raw=true)

测试pac是否代理成功——百度“ip”

![](https://github.com/qingshuisiyuan/electron-ssr-backup/blob/master/img/ubuntu/4.png?raw=true)

测试全局是否代理成功——百度“ip”

![](https://github.com/qingshuisiyuan/electron-ssr-backup/blob/master/img/ubuntu/5.png?raw=true)

### 系统自动代理

在系统设置-网络设置-代理设置改为自动一样可用

（笑，系统设置那一步白设置了？）

不，在某些Debian系列中，你还真得手动设置，自动无效

本应用使用`gsetting`设置系统代理，所以有些Linux系统无法使用该功能

### 某些软件提示https错误

如git就提示过

具体原因不知道

尝试使用以下方法解决：

1. 更改系统代理方式为自动
2. 使用pac
