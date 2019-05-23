![简单图床示例](https://img.545141.com/public/data/2019/05/5ce6915f50a1a.png "简单图床示例")
![简单图床示例](https://img.545141.com/public/data/2019/05/5ce6b41416a2b.png "简单图床示例")

## EasyImage 简单图床
> 支持多文件上传,异地上传,api上传,简单无数据库,返回图片url,markdown,bbscode,html的一款图床程序
演示地址：[https://img.545141.com](https://img.545141.com "PHP多图长传程序2.4.3")
之前一直用的图床程序是:[PHP多图长传程序2.4.3](http://www.mycodes.net/48/4925.htm "PHP多图长传程序2.4.3")
由于版本过老并且使用falsh上传，在当前html5流行大势所趋下，遂利用基础知识新写了一个以html5为默认上传并且支持flash,向下兼容至IE9。

<b>注意：</b>

1. 装之前先使用服务器打开check.php检查扩展是否都安装！
2. js不要设置分片上传大小，此会导致部分图片上传失败。
3. 使用前请注意先修改config.php中的domain域名。
4. 安装正常后请修改登录上传密码和管理密码！具体如何修改可以打开config.php里边有注释。
5. 如果无法登陆管理界面或上传图片，请先打开check.php检查扩展。
6. 默认我会给你设置成最优方案，如果需要其他的功能，比如异地存储和api上传，请仔细查看config.php文件


##### 一年未更新了，这次带来了全新版本2.0！
- 在继承上个版本（1.6.4）的基础上进行了全新优化
- 修复上传经常失败的问题
- 删除一些不常用但会增加功耗的过程 （删除的在下边会有标记）
- 全新的压缩 将文件继续缩小
- 全新的目录系统，精简代码
- 设置仅允许在config.php修改，注释更加明了，即使没有代码基础也可以操作
- 增加新的文件管理系统

<hr />

#### 功能支持：

- 支持设置图片质量
- 支持上传图片转换为指定格式
- 支持设置图片指定宽/高
- 支持限制最低宽度/高度上传
- 支持静态文件CDN/本地切换
- ~~支持开启/关闭浏览最近上传图片~~ -> 使用最新的管理系统
- 支持仅登录后上传
- 支持设置广告
- 支持网站统计 请将统计代码放入:public/static/hm.js
- 图片管理(删除，查看)
- 支持上传图片至远程服务器(异域存储)
- 支持开启/关闭api上传

#### api上传示例：
参数：

| 参数名称 | 类型 | 是否必须 | 说明 |
| :------------: | :------------: | :------------: | :------------: |
| file | file | 是 | 表单名称 |

html form上传示例:
```html
<form enctype="multipart/form-data" method="POST" action="https://img.545141.com/file.php">
        <label>选择文件</label>
        <input type="file" name="file">
        <input type="submit" value="提交">
</form>
```
api上传成功后返回json：
```json
{"result":"success","url":"https:\/\/img.545141.com\/public\/data\/2019\/05\/5ce64172d24fa.png"}
```
如果关闭api上传，则什么都不显示。
#### 异地上传[跨域上传] 教程：
1. 开启config.php的跨域上传功能
2. 将 crossdomain 文件夹内和根目录的config.php拷贝到新的服务器
3. 新的服务器上把所有文件和目录赋予0777权限
4. 修改新服务器的 config.php 的 **"domain"**为当前域名
5. 修改原服务器的 config.php 的 'CDomains' 为 http：//www.新域名.com/crossdmain/file.php

##### 异地上传举个栗子：
- 我有一个域名A.com，想上传到B.com
1. 修改A.com服务器的config.php 'crossDomain'=>true,
2. 复制corssdomain文件夹和A.com的config.php到B.com同一目录下 并赋予777权限(chmod -R 777 /B.com/*)
3. 修改B.com的config.php 'domain'=>'https://B.com'
4. 修改A.com的config.php'CDomain'=>'https://B.com/corssdomain/'
- 这样就添加了异域上传，如果有什么改动的话，可以直接复制config.php到B.com
- 因为异域上传存在任意上传的功能，强烈建议确定A.com服务器后修改file.php中的
header('Access-Control-Allow-Origin:*')
将其修改为:
header('Access-Control-Allow-Origin:https://A.com/')
指定域名可以限制别人上传图片！(并不能保证完全能防止，毕竟可以伪造)

---
* 2019-5-23 v2.0
- 在继承上个版本（1.6.4）的基础上进行了全新优化
- 修复上传经常失败的问题
- 删除一些不常用但会增加功耗的过程
- 全新的压缩 将文件继续缩小
- 全新的目录系统，精简代码
- 设置仅允许在config.php修改，注释更加明了，即使没有代码基础也可以操作
- 增加新的文件管理系统，支持增删改查
- ~~支持文字/图片水印 可自定义文字颜色~~
- ~~支持文字水印背景颜色~~
- ~~支持文字水印透明度~~
- ~~支持删除远程上传文件~~ -> 不再支持删除远程文件
- ~~(支持开启/关闭api自定义文字水印)~~
- ~~支持删除自定义删除图片(仅管理员)~~

* 2018-8-17 v1.6.4
- 支持删除远程上传文件
- 更改字体
- 添加api/远程上传 标识
* 2018-8-16 v1.6.3
- 支持开启/关闭api上传(支持开启/关闭api自定义文字水印)
- 修复权限错误
- 修复二级目录引入错误

* 2018-8-8 v1.5.3
- 添加上传图片至远程主机
- 修复逻辑

* 2018-8-6 v1.4.3
- 添加网站统计
- 添加删除上传文件
- 调整config.php

* 2018-8-5 v1.4.2
- 添加仅登录后上传
- 修复一处逻辑错误
- 修复一个漏洞

* 2018-8-4 v1.3.2
- 添加广告设置
- 完善引入机制

* 2018-8-3 v1.2.2
- [重要]修复水印图片不能添加
- 添加随机浏览上传图片 可以设定浏览数量和关闭浏览
- 优化代码，删除无用文件
- 完善一键CDN静态文件

* 2018-08-02 v1.1.2
- [重要] 修复gif上传添加水印成静态的问题
- 修复文字水印背景色不显示问题
- 修复在linux下的权限错误
- 一些优化更改

* 2018-08-01 v1.0.1
- 更改相关文件目录
- 优化代码

* 2018-07-30 v1.0.0
- 最初模型

#### 兼容性
文件上传视图不支持IE9以下的浏览器,api不限制。建议php5.6及以上版本,需要服务器支持Fileinfo, iconv ,zip和mbstring扩展,如果缺失会导致无法访问管理面板以及上传图片。

文件上传视图提供文件列表管理和文件批量上传功能，允许拖拽（需要 HTML5 支持）来添加上传文件，支持上传大图片，优先使用 HTML5，旧的浏览器自动使用Flash和Silverlight的方式兼容。
<hr />

 - 感谢: [verot](https://www.verot.net "verot" )提供非常好用的class.upload.php上传类
 - 感谢: [ZUI](http://zui.sexy/ "ZUI" ) 提供css框架
 - 感谢:[tinyfilemanager](https://github.com/prasathmani/tinyfilemanager "tinyfilemanager" ) 提供的文件管理
 - 本源码遵循 GNU Public License