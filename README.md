# 音乐搜索器

## 说明

多站合一音乐搜索解决方案，由麦葱（https://github.com/maicong/music/releases）开发，支持搜索试听以下网站音乐：

[网易云音乐](http://music.163.com) [QQ音乐](http://y.qq.com) [酷狗音乐](http://www.kugou.com) [酷我音乐](http://www.kuwo.cn) [虾米音乐](http://www.xiami.com) [百度音乐](http://music.baidu.com) [一听音乐](http://www.1ting.com) [咪咕音乐](http://music.migu.cn) [荔枝FM](http://www.lizhi.fm) [蜻蜓FM](http://www.qingting.fm) [喜马拉雅FM](http://www.ximalaya.com) [5sing原创](http://5sing.kugou.com/yc) [5sing翻唱](http://5sing.kugou.com/fc)

数据调用的是各网站的 API 接口，有的接口并不是开放的，随时可能失效，本项目相关代码仅供参考。

## 演示

http://music.wqdy.top

## 部署

<a href="https://vercel.com/new/clone?demo-description=音乐搜索器&amp;demo-title=音乐搜索器&amp;demo-url=https://music.wqdy.top&amp;project-name=music&amp;s=https://github.com/wqdygkd/music&amp;repository-name=music&amp;from=templates&amp;demo-image=https://og-image.vercel.app/**Vercel**%20%2B%20**PHP**.jpeg?theme=light&md=1&fontSize=100px&images=https%3A%2F%2Fassets.vercel.com%2Fimage%2Fupload%2Ffront%2Fassets%2Fdesign%2Fvercel-triangle-black.svg&images=https%3A%2F%2Fsimpleicons.vercel.app%2Fphp%2F595C96&heights=200&heights=350" rel="nofollow"><img src="https://camo.githubusercontent.com/5e471e99e8e022cf454693e38ec843036ec6301e27ee1e1fa10325b1cb720584/68747470733a2f2f76657263656c2e636f6d2f627574746f6e" height="24" data-canonical-src="https://vercel.com/button" style="max-width: 100%;"></a>

## 解决方案

**1. 提示数据获取失败**

方案1：

```
修改 index.php 文件里的 MC_PROXY 为您的代理地址
将 core/music.php 里需要代理的 URL 'proxy' => false 改为 'proxy' => true
```

方案2：

```
在 core/music.php 里查找 setTimeout，将其后面的数值 20 改为更大。
在 static/js/music.js 里查找 `timeout`，将其数值 30000 改为更大。
```

方案3：

```
服务器要支持 curl。
更换服务器，选择延迟更低的服务器。
```

**2. 播放器显示 `Error happens ╥﹏╥`**

音乐链接为空

```
1. 音乐需要付费才能收听
2. 版权限制，外站无法获取
3. 服务器 IP 所在地不在源站允许的区域
4. 音乐下架了，链接被去除
```

音乐链接不为空

```
1. 当前 IP 所在地因版权限制而无法播放
2. 音乐格式浏览器无法正常解析
```

**3. 国内接口优化**

如果你的网站在国内，打开 [/index.php](index.php)，将 `define('MC_INTERNAL', 0);` 修改为 `define('MC_INTERNAL', 1);`，这样就可以取到咪咕和网易云音乐的 320k 音频了。

## 更新日志

请查看 [CHANGELOG.md](CHANGELOG.md)

## 免责声明

1. 本站音频文件来自各网站接口，本站不会修改任何音频文件
2. 音频版权来自各网站，本站只提供数据查询服务，不提供任何音频存储和贩卖服务
3. 本项目代码仅供学习交流，不得用于商业用途，如有侵犯与代码贡献人员无关

## 开源协议

The MIT License (MIT)
