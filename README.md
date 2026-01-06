# wine-patches-docs
Wine patches and documentation.wine补丁与文档。

此项目用于整理相对通用的wine构建补丁解决方案。

# 让wine正常调用gstreamer解码unity游戏的视频！

- 原理：比对wine与proton的dlls/mfplat/main.c[proton wine => target wine]

- 其他方案：目前无法通过安装软件解码器的形式解决，禁用gst的方案无效。

- wine开发进展：最新版wine10.20中仍然未修复此问题

## 补丁：

- 前置要求：wine10.0+

- [10.0=<x=<10.4](mfplat-no-dxgi-mgr/wine_do_not_create_dxgi_manager_device.patch)

- [10.4<x<?](mfplat-no-dxgi-mgr/wine_do_not_create_dxgi_manager_device-2.patch)

- Old: wine9 <= 未测试

- [9=<?<10](mfplat-no-dxgi-mgr/wine9_do_not_crate_dxgi_manager_device.patch)
