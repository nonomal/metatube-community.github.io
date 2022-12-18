# FAQ (常问问题)

## Q：插件怎么不显示？

请先确保：

1. Jellyfin/Emby均为**最新的**稳定版，看[这里](https://github.com/metatube-community/jellyfin-plugin-metatube/wiki/%E6%8F%92%E4%BB%B6%E5%AE%89%E8%A3%85#%E5%AE%89%E8%A3%85%E4%B9%8B%E5%89%8D)。
2. 插件目录放对。
3. 插件权限正确（权限不对日志会报错`Permission Denied`）。

还是不行：

1. 看一下Jellyfin/Emby的日志具体报错。
2. 再不行，Issues报告BUG。

## Q：如何配置代理？

参阅[关于代理](https://github.com/metatube-community/jellyfin-plugin-metatube/wiki/%E5%85%B3%E4%BA%8E%E4%BB%A3%E7%90%86)。

## Q：为什么有些影片刮不出来？

MetaTube支持二十多个官方数据源，基本涵盖了所有JAV的范畴，所以很少存在由于数据源匹配不到的问题。

1. 确保文件命名规范且正确，参考[命名规范](https://github.com/metatube-community/jellyfin-plugin-metatube/wiki/%E5%91%BD%E5%90%8D%E8%A7%84%E8%8C%83)。
2. 确保网络正常没有炸。
3. 仍然刮不到可以去官网找一下源影片是否存在。
4. 如果官网都找不到，那就只能手动添加数据了。

> PS：有些MGS的影片，通常以数字开头，如`200GANA-2704`，但是某些网站（如JavDB）会将前面的数字去掉，变成`GANA-2704`，导致搜索不到，这纯属文件命名规范的锅，手动修改后即可正确识别。另外，部分台湾的IP地址似乎不能访问MGS网站，所以可能需要代理。

## Q：为什么搜索时不能显示图片？

如果你用的是Emby，那这可能是Emby的一个~~BUG~~特性，因为如果`metatube-server`服务端部署在本地且没有使用正常的HTTPS时，Emby就不会去加载图片。

解决方案：

1. 本地加个有SSL的反向代理。
2. 使用VPS/Cloud重新部署有SSL证书的服务端。

## Q：为什么不支持JavDB刮削源？

1. JavDB对爬虫不友好，经常更新反爬，有时也会**Ban IP**。
2. JavDB没有简介，不如官方网站信息全面。

## Q：插件计划支持Plex吗？

> June 2022 Update: Plex is phasing out plugins — especially those that require UI support or play content (like streaming plugins). Plex’s representative couldn’t give me an exact date when plugin support would be removed completely but told me that you should no longer rely on plugins to work. I will keep testing and update this page when I know more.

Plex官方即将取消插件支持，所以应该不会开发Plex插件。

## Q：为什么翻译不出来？

确保：

1. 选择正确的翻译模式，不能是`Disabled`。
2. 填对正确的API Key等信息。
3. 看Jellyfin/Emby日志报错信息。

## Q：为什么搜不出`19xx`和`20xx`结尾的番号？

这是个Emby的bug，它会把这些数字识别成年份，插件无法正确获得完整的番号最终导致刮削失败。

解决办法：手动搜索时在番号后面加上`#`，例如：`MXGS-1997#`。