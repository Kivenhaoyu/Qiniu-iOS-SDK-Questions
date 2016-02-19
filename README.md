#七牛云存储iOS SDK 常见问题
##目录

- [CocoaPods接入问题](#questions about CocoaPods)
       - [CocoaPods安装](#install CocoaPods)
       - [用CocoaPods安装七牛SDK版本不是当前版本](#version is wrong)
- [配置问题](#questions about configuration)
       - [CocoaPods安装](#install CocoaPods)
       - [用CocoaPods安装七牛SDK版本不是当前版本](#version is wrong)
- [使用问题](#questions about using)
       - [CocoaPods安装](#install CocoaPods)
       - [用CocoaPods安装七牛SDK版本不是当前版本](#version is wrong)
- [其他](#others)
       - [CocoaPods安装](#install CocoaPods)
       - [用CocoaPods安装七牛SDK版本不是当前版本](#version is wrong)

   

<a name='questions about CocoaPods'></a>
##CocoaPods接入问题

当前七牛云存储iOS SDK接入，推荐使用CocoaPods，但是还是会遇到这样或者那样的问题

<a name='install CocoaPods'></a>
###CocoaPods安装
问：七牛iOS推荐CocoaPods第三方管理下载，这里的Cocoa
答：CocoaPods安装，目前网上已经有很全面的介绍了，这里就不一一赘述，有需要的可以访问[CocoaPods安装使用](http://code4app.com/article/cocoapods-install-usage),这里有详细的教程和解释。

<a name='version is wrong'></a>
###用CocoaPods安装七牛SDK版本不是当前版本
问：用CocoaPods下载的七牛SDK不是当前最新版本

答：1，检查当前CocoaPods版本是否为最新版
      在终端中输入
      
      ```ruby
      $ pod --version
      ```
      
      如果是最新版本，请直接跳至第二步，CocoaPods未更新至最新版本，直接用命令行更新（安装）步骤
      
      ```ruby
      $ sudo gem update --system // 先更新gem，国内需要切换源
      $ gem sources --remove https://rubygems.org/
      $ gem sources -a http://ruby.taobao.org/
      $ gem sources -l
      \*\*\* CURRENT SOURCES \*\*\*
      http://ruby.taobao.org/
      $ sudo gem install cocoapods // 安装cocoapods
      $ pod setup
      ```
      
      再次查看版本
      
      ```ruby
      $ pod --version
      ```
      
      查看是否是最新版本
      之后重新在项目下输入
      
      ```ruby
      $ pod install
      ```


    2，如果版本为最新版本，请清理当前CocoaPods的缓存
       先删除全局的缓存：
       
       ```ruby
       $ sudo rm -fr ~/Library/Caches/CocoaPods/
       $ sudo rm -fr ~/.cocoapods/repos/master/
       ```
       还不行的话就把当前 Pods 目录清空：
       ```ruby
       $ sudo rm -fr Pods/
       ```
       之后再运行：
       ```ruby
       $ pod install
       ```

<a name='questions about configuration'></a>
##配置问题

<a name='questions about configuration'></a>
###关于https问题
iOS 9+ 强制使用https，需要在project build info 添加NSAppTransportSecurity类型Dictionary。在NSAppTransportSecurity下添加NSAllowsArbitraryLoads类型Boolean,值设为YES。如图
