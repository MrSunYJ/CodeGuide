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

- 参数一和二：七牛云个人中心的**AccessKey** 和 **SecretKey**    (很重要保护好)。对应目录1.4**

- 参数三：我们在七牛云创建存储空间的【存储空间名】。对应目录**1.1**

- 参数四：七牛云给我们的测试域名地址，30会回收那个。记得加上前缀`http://`。

  ![image-20210111191425423](http://qmrnd6f3u.hd-bkt.clouddn.com/typora/image-20210111191425423.png)

- 参数五：存储区域，每次创建存储区域都会让我们选择，填写对应的地区简称就可以，对应目录**1.3**

- 参数六：没有需求不要填写，保持默认

- 参数七：就相当于目录的划分，子目录，如有需要可以添加（不同文章的图片放一起）。

## 3.Typora实现图片上传

- **文件--->偏好设置--->图像**

  ![image-20210111192157506](http://qmrnd6f3u.hd-bkt.clouddn.com/typora/image-20210111192157506.png)

- 测试Typora自动上传图片功能。点击**文件--->偏好设置--->图像--->**

  ![image-20210111192458476](http://qmrnd6f3u.hd-bkt.clouddn.com/typora/image-20210111192458476.png)

  

## 4.七牛云绑定备案域名设置

### 阿里云域名申请和备案

- 域名的购买：https://wanwang.aliyun.com/domain/searchresult/
- 域名购买后**一定要先实名认证**。申请实名认证之后三天内先不要备案，因为很有可能备案不通过。

- 有的小伙伴可能主机和域名不是同一个账号(当然如果是同一个账号肯定没有问题)。我的就不是同一个账号依旧备案成功。

- 备案域名是否一定要有主机？目前不是特别清楚，但是备案需要填写(必填)，如果找不到别的方式，可以购买一个主机和域名一起备案。下面是大致流程。阿里云的审核基本当天或者第二天就会给你反馈。

  ![image-20210111222139494](http://blog.sunyj.online/typora/image-20210111222139494.png)

### 备案域名绑定七牛云

- 备案通过之后，我们尽量使用我们的二级域名，什么是二级域名？比如我们备案的域名是xxx.com，那么我们在进行七牛云域名绑定的时候可以使用blog.xxx.com，aaa.xxx.com，bbb.xxx.com等这些都可以被称为二级域名。

- 进入到七牛云的对象存储。

  ![image-20210111224550982](http://blog.sunyj.online/typora/image-20210111224550982.png)

- 填写加速域名(这里如果备案过的话不会出现提醒)。

  ![image-20210111224749683](http://blog.sunyj.online/typora/image-20210111224749683.png)

- 绑定完成之后我们需要使用CNAME的值去域名申请的位置进行解析。

  ![image-20210111225509221](http://blog.sunyj.online/typora/image-20210111225509221.png)

- 进行CNAME的二级域名的解析。

  域名--->解析--->解析设置--->添加记录

  ![image-20210111225753069](http://blog.sunyj.online/typora/image-20210111225753069.png)

  ![image-20210111230034688](http://blog.sunyj.online/typora/image-20210111230034688.png)

- 到这里基本就差不多了。之后修改我们的PicGo的部分配置。

  ![image-20210111230300568](http://blog.sunyj.online/typora/image-20210111230300568.png)

- 易错点：

  检查PicGo的【设定访问网址】和【确认存储区域】

  ![image-20210111230512892](http://blog.sunyj.online/typora/image-20210111230512892.png)

## 5.资料

- Typora获取
  - 官网：https://www.typora.io/
  - 网盘：链接：https://pan.baidu.com/s/1HmwtDoOwsFpt47iYJgdOlw   提取码：k6ih 
- PicGo获取
  - github地址:https://github.com/Molunerfinn/PicGo/releases/tag/v2.2.2
  - 网盘地址：链接：https://pan.baidu.com/s/1xm3psOzI3vewdYWa3duSAg   提取码：yzh6 
- 如有网盘失效公众号【CodeGuide】回复`typora`

