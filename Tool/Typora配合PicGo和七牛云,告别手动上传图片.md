# Typora配合PicGo和七牛云实现图床

>如需资料至文章底部获取。

## 0.为什么需要图床？

>有写作习惯的小伙伴一定知道 MarkDown ，写出来的文章简洁大方，重点是上手难度很低。(建议不会的小伙伴学一下)
>
>知道并且喜欢Typora的小伙伴应该都知道，在图片上传上的痛楚。每次在平台发布文章都要在手动处理一下，非常的麻烦。

- **Typora+PicGo+七牛云**就是解决这一问题的最好方式之一。(还有Typora+PicGo+Gitee/Github等实现方式)。
- **Typora(0.9.86版本以上)**，支持MarkDown的一款具有代表性的软件。
- **PicGo(推荐2.2.2版本)**，一款用于管理图片的工具，一般用于图床的管理。
- **七牛云(云存储)**，用来存储我们文章中上传的图片(互联网可访问)。

## 1.七牛云配置对象存储

- **1.1**  注册并创建对象存储空间，注册成功就送10G的免费存储空间。一般文章存储图片是够用了。

  补全存储空间名字，选择存储区域一会会用到。

  ![image-20210111183917575](http://blog.sunyj.online/typora/image-20210111183917575.png)

- **1.2**  一般储存空间创建成功之后，我们创建的存储空间的地址域名有效期为30天。后面会讲到重新绑定指向备案域名。

  ![image-20210111185103588](http://blog.sunyj.online/typora/image-20210111185103588.png)

- **1.3**  七牛云的存储对象地区对应表(PicGo配置地区存储区域会用到)：

  | 存储区域 | 地域简称 | 上传域名                                                     |
  | :------- | :------- | :----------------------------------------------------------- |
  | 华东     | z0       | 服务器端：`http(s)://up.qiniup.com`        客户端： `http(s)://upload.qiniup.com` |
  | 华北     | z1       | 服务器端：`http(s)://up-z1.qiniup.com`  客户端：`http(s)://upload-z1.qiniup.com` |
  | 华南     | z2       | 服务器端：`http(s)://up-z2.qiniup.com`  客户端：`http(s)://upload-z2.qiniup.com` |
  | 北美     | na0      | 服务器端：`http(s)://up-na0.qiniup.com` 客户端：`http(s)://upload-na0.qiniup.com` |
  | 东南亚   | as0      | 服务器端：`http(s)://up-as0.qiniup.com` 客户端：`http(s)://upload-as0.qiniup.com` |

- **1.4**  七牛云**AccessKey** 和 **SecretKey**获取

  ![image-20210111184512845](http://blog.sunyj.online/typora/image-20210111184512845.png)

## 2.PicGo配置七牛云参数

- PicGo基本参数的配置

  ![image-20210111185944574](http://qmrnd6f3u.hd-bkt.clouddn.com/typora/image-20210111185944574.png)

- PicGo配置的前两个参数就是七牛云个人中心

## 3.Typora实现图片上传

## 4.资料

- Typora获取
  - 官网：https://www.typora.io/
  - 网盘：链接：https://pan.baidu.com/s/1HmwtDoOwsFpt47iYJgdOlw   提取码：k6ih 
- PicGo获取
  - github地址:https://github.com/Molunerfinn/PicGo/releases/tag/v2.2.2
  - 网盘地址：链接：https://pan.baidu.com/s/1xm3psOzI3vewdYWa3duSAg   提取码：yzh6 
- 如有网盘失效公众号【CodeGuide】回复`typora`

