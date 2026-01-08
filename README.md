# wine-patches-docs
Wine patches and documentation.wine补丁与文档。

此项目用于整理相对通用的wine构建补丁解决方案与教程。

# 通过合理的变量设置让速度与功能得以提升！

- [环境变量(通用)](environment.txt)

# 函数库（DLLOVERRIDE）

可以通过winecfg直接图形化完成配置！

举个例子这是你的游戏目录：

Game {
    game.exe
    d3d9.dll <= dxvk
    ...
}

然而wine在发现d3d9.dll的这个动态库实际上wine的lib/*windows*/下也有这个文件（wined3d），然后你会发现dxvk根本不起作用，那么此时需要在winecfg里面添加 d3d9（或者d3d9.dll），原装先于内建（n>b），那么就会优先调用游戏目录其次是内置的dll，反之亦然。这对于包含同名dll的游戏尤为有效，或者在安装dll相关动态库时，比如vc运行库。

部分galgame的字体显示问题如果目录下存在version.dll这个文件就可以通过设置内建先于原装彻底解决。

wine通常默认调用内建的动态库。

### 工具：

- [msvcrt.bat(VC库)](dlloverride/msvcrt.bat)

- [proton-override](dlloverride/proton-override.bat)

- [dll.reg(通用)](dlloverride/dll.reg)

### 相关文档：

- [http://xian1.net.cn/manul/jsj/wine/dll-overrides.html](http://xian1.net.cn/manul/jsj/wine/dll-overrides.html)


# 让wine正常调用gstreamer解码unity游戏的视频！

制作：比对wine与proton的dlls/mfplat/main.c[proton wine => target wine]

其他方案：目前无法通过安装软件解码器的形式解决，禁用gst的方案无效。

wine开发进展：最新版wine10.20中仍然未修复此问题

### 补丁：

前置要求：wine10.0+

- [10.0=<x=<10.4](mfplat-no-dxgi-mgr/wine_do_not_create_dxgi_manager_device.patch)

- [10.4<x<?](mfplat-no-dxgi-mgr/wine_do_not_create_dxgi_manager_device-2.patch)

Old: wine9 <= 未测试

- [9=<?<10](mfplat-no-dxgi-mgr/wine9_do_not_crate_dxgi_manager_device.patch)
