# SublimeC51Guide
Keil自带的编辑器太烂，这是用Sublime Text来开发8051程序的教程

1 安装Sublime Text 3，建议在官网下载绿色portable版本。此正版几百大洋，诸位自己想办法。

2 汉化
* 复制此文件夹下的`Default.sublime-package`到`Sublime Text 3\Data\Installed Packages\`下

3 关闭自动更新
* 打开菜单`Preferences->设置-用户`,在"{}"中间输入如下内容：
	"update_check": false,

4 安装Package Control
* 打开按`Ctrl+'`(数字键1左边的按键)，调出命令行窗口；
* 输入如下命令，回车：
```
import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```
* 重启Sublime，在`Preferences`菜单下就有`Package Control`菜单项了



4 安装普通插件
* 按`Ctrl+Shfit+P`调出PackageControl面板，选择`Install Package`，输入相应的插件名称即可。
* 推荐插件：
```
	C Improved
	Alignment
	All Autocomplete
	BracketHighlighter
	DocBlockr
	HexViewer
	SideBarEnhancements
	WordHighlight
	SublimeAStyleFormatter
	ConvertToUTF8
	ClangAutoComplete
```

5 安装C51必须插件
* [Keil-Compiler](https://github.com/bingdianfeishui/sublime-Keil-Compiler)
* [Hex-Bin-System](https://github.com/bingdianfeishui/hex-bin_system)
* 安装方法：

打开网页，点击绿色的"clone or download"，然后DownloadZip，将下载的文件解压到`Sublime Text 3\Data\`下

6 更改语法高亮，以识别`sbit` `sfr` `interrupt`等

下载此文件夹下的`C Improved.tmLanguage`文件，复制到`Sublime Text 3\Data\Packages\User\`下

7 安装一些常用的代码段【可选】

下载此文件夹下的`C51`文件夹，复制到`Sublime Text 3\Data\Packages\User\`下



##添加Sublime Text 3到右键菜单

此处不采用直接修改注册表的方法，而采用inf文件安装的方法。

* 在Sublime Text 3文件夹下新建一个`*.inf`文件，打开并输入如下内容：

```
[Version]
Signature="$Windows NT$"

[DefaultInstall]
AddReg=SublimeText3

[SublimeText3]
hkcr,"*\\shell\\SublimeText3",,,"用SublimeText3打开(&W)"
hkcr,"*\\shell\\SublimeText3\\command",,,"""%1%\sublime_text.exe"" ""%%1"" %%*"
hkcr,"Directory\shell\SublimeText3",,,"用SublimeText3打开(&W)"
hkcr,"*\\shell\\SublimeText3","Icon",0x20000,"%1%\sublime_text.exe, 0"
hkcr,"Directory\shell\SublimeText3\command",,,"""%1%\sublime_text.exe"" ""%%1"""

```
* 保存后，右键改inf文件，选择"安装"即可。

