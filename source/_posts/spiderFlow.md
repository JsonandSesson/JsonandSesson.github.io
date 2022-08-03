---
title: spiderFlow可视化爬虫工具
tags: ['web爬虫']
categories: ['爬虫','可视化工具']
date: 2022-05-06 10:46:00
swiperImg: '/medias/1.jpg'
img: '/medias/1.jpg'
swiper: true # 将改文章放入轮播图中
toc: true
tocOpen: true 
copyright: true
top: true # 文章置顶
---

### **介绍**
---
---
spider-flow 是一个爬虫平台，以图形化方式定义爬虫流程，无需代码即可实现一个爬虫  
![spdierflow_index](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/spdierflow_index.png)
详情见[官方文档](https://www.spiderflow.org/changelog.html)  
可以下载官方代码包[相关代码](https://github.com/ssssssss-team/spider-flow)
### **特性**
---
--- 
+ 支持css选择器、正则提取
+ 支持JSON/XML格式
+ 支持Xpath/JsonPath提取
+ 支持多数据源（mysql/redis/mongodb）、SQL select/insert/update/delete
+ 支持爬取JS动态渲染的页面
+ 支持代理
+ 支持二进制格式
+ 支持保存/读取文件(csv、xls、jpg等)
+ 常用字符串、日期、文件、加解密、随机等函数
+ 支持流程嵌套
+ 支持插件扩展(自定义执行器，自定义函数、自定义Controller、类型扩展等）
+ 支持HTTP接口

### **插件**
---
--- 
+ redis插件
+ mongodb插件
+ IP代理池插件
+ OSS插件
+ OCR插件（目前仅支持百度OCR统一文字识别）
+ Selenium插件（集成在maven中）

### **安装**
---
---
windows环境的安装很简单，请参考官方文档，下面主要说说linux环境
> 这里我用的是centos8.2(版本应该影响不大)。其他小伙伴请参考  
> 相关的爬虫驱动使用chrome
```
 cat /etc/centos-release #查看当前版本
```

1. ####安装chrome
```
 curl https://intoli.com/install-google-chrome.sh | bash
 ldd /opt/google/chrome/chrome | grep "not found"
```
安装完成后，执行如下测试命令，会在当前目录下生成一张百度的图片
```bash
google-chrome-stable --no-sandbox --headless --disable-gpu --screenshot https://www.baidu.com/
```

2. ####安装 chromedriver
- [x] 查看当前chrome浏览器版本 
 ```bash
 google-chrome-stable --version
 ```
![](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/spriderflow_chrome_version.png)
- [x] 根据指定版本下载chromedriver
  [下载地址](https://registry.npmmirror.com/binary.html?path=chromedriver/)  
  ![](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/chromedrive.png)
  官方提供的是zip格式，如果服务器不存在请先安装 unzip
   ```bash
     # 安装unzip
     yum install unzip
     # 解压
     unzip chromedriver_linux64.zip
   ```
- [x] 建立软连接或者复制、移动过去(推荐直接复制过去，省事)
     ```bash
     ln -s 源地址 /usr/bin/chromedriver
     mv chromedriver /usr/bin/chromedriver
     ```
  查看chromedriver版本
     ```bash
    chromedriver --version
     ```

3. ###项目相关配置
---
---
application.properties相关配置
- [x] selenium 配置
     ```bash
    #设置chrome的WebDriver驱动路径，下载地址：http://npm.taobao.org/mirrors/chromedriver/，注意版本问题
    selenium.driver.chrome=/usr/bin/chromedriver
    #设置fireFox的WebDriver驱动路径，下载地址：https://github.com/mozilla/geckodriver/releases
    #selenium.driver.firefox=E:/driver/geckodriver.exe
     ```

- [x] 定时任务配置
  ```bash
    #设置为true时定时任务才生效
    spider.job.enable=true
  ```

- [x] 其他数据库地址配置的，相关库需要首先导入
  项目下的sql文件导入数据库中
  ![](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/spriderflow_db.png)
  ___如果安装了其他插件，如百度ocr，需要另外导入sql，在ocr包下的db目录下___
  
4. ###项目实战
    > 以下我已爬取80s电影网数据为例子([网站地址](https://www.80dytta.com/movie/0-0-0-0-0-1))
   - 具体流程图大致为  
     1. 定义开始节点
     2. 定义请求前变量
        ![](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/OWRCWS%5DNPYGN%25GINKZV%5D096.png)
     3. 设置请求配置
        ![](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/3%7DDX_KLFO%24WQ%40GNM928%5BL9D.png)
     4. 定义变量获取页面相关返回值
        具体的语法请参考官方文档 [SpiderResponse](https://www.spiderflow.org/classes/spiderresponse.html#element)
        ![](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/684%5B%5B4DZ%5BQYWHFFNLH%28M52G.png)
     5. 循环设置
        ![](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/%25IFL%605%40312%40E2THYP%28X~__K.png)
     6. 定义输出变量，解析每个节点
        此时 movieList 是一个List<Element>,我们要拿到当前循环的Element，获取电影中我们需要的每个属性
        ![](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/%24J~Y1WZW1%5DMAO%246CS%60AU0_2.png)
     7. 输出显示以及入库操作  
        - 将根据上一步定义的变量，指定输出。如果需要插入数据库，需要指定数据源。
        ![](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/ICLR2H2EU07C%24OBZ%5D2C7U%25W.png)
        - 数据源配置以及数据库设计
          {% gallery %}
          ![数据源配置](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/EI6%5DFX%28EE%60EULZT%24%40%7B_~WN5.png)
          ![表设计](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/D%7B%4032VN2L~U9MZ8MSHDE56E.png)  
          {% endgallery %} 
     #### 测试相关使用
     {% gallery %}
        ![执行结果](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/IKQ0%5B1QM%28%7BK%24LY%7B%60%7BN_BHZR.png)
     {% endgallery %}
     可以看到控制台已经输出日志，检查数据库保存情况
     ![img.png](https://raw.githubusercontent.com/JsonandSesson/blog-img/main/img.png)
     可以看到相关数据已经成功传入。
5. ### 其他坑
   > 如果报错死循环了，可能是因为没有配置 死循环监测（默认5000）
     ```bash
     #死循环检测(节点执行次数超过该值时认为是死循环)默认值为5000
     spider.detect.dead-cycle=1000000
     ```
