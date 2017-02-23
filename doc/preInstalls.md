Capistrano是一种通过ssh向多个服务器部署web应用的一种框架和工具。具体更详细的介绍，大家可以登录[官方网站][4]或其它相关网站进行了解。

# 软件准备

1. 操作系统：linux

2. Ruby >`2.*`（官方要求Capistrano3.0+运行条件，必须Ruby>2.0）

3. Rubygem >`2.*`

4. capistrano >`3.*`

# 安装

- linux发行版之间有差异，安装Ruby不一（且Capistrano 3 官方要求ruby>2.0），特此对Ubuntu和CentOS单独列出安装Ruby和rubygems的方法

## Ubuntu 安装ruby 和 Rubygem

运行一条命令即可：

```
sudo apt-get update
sudo apt-get install ruby-full rubygems
```

![zan001.jpg][1]

提示我已安装了当前Ubuntu最稳定的ruby2.3版本。


## CentOS 安装ruby

### 注：由于CentOS yum库ruby版本过低（如下图），无法满足Capistrano 3官方运行要求，只能通过编译安装ruby>2.0版本。

![zan002.png][2]

```
wget https://cache.ruby-lang.org/pub/ruby/2.4/ruby-2.4.0.tar.gz    #下载(若没有wget,请先安装wget：`yum install -y wget`)
tar xf ruby-2.4.0.tar.gz                                           #减压
yum install -y gcc-c++ zlib zlib-devel openssl-devel               #安装依赖
./configure && make && make install                                #编译安装

```
## CentOS 安装rubygems

```
wget https://rubygems.org/rubygems/rubygems-2.6.10.tgz`
tar xf rubygems-2.6.10.tgz
cd rubygems-2.6.10
ruby setup.rb
```

# 安装capistrano

## 方法1：
执行命令：

```
gem install capistrano
```
![zan002.jpg][3]

提示我已近安装了`capistrano-3.7.2`，这也是当前最新版本了。

## 方法2：
执行命令：

```
git clone https://github.com/capistrano/capistrano.git` 
cd capistrano
gem build *.gemspec 
gem install *.gem
```

更多安装方法请参考[Captrisano官网][4]

# 查看安装信息

```
ruby -v
gem -v
cap -v
```
![zan003.jpg][5]

# 总结

Capistrano依赖zlib和openssl，安装ruby前需要将这两个软件包安装好，这样安装过程才会比较顺利。
Capistrano依赖于使用基于密钥（即无密码）身份验证的SSH连接到您的服务器。你需要提前做这个工作，然后才能使用Capistrano.
同样，您的服务器可能需要安装支持软件，然后才能执行部署。除了SSH之外，Capistrano本身没有任何要求，但您的应用程序可能需要数据库软件，像Apache或Nginx这样的Web服务器，以及Java，Ruby或PHP等语言运行库。这些服务器配置步骤不是由Capistrano完成的,需要你提前搭建好。


  [1]: https://github.com/ShaoZeMing/capistrano3-doc/blob/master/img/zan001.jpg
  [2]: https://github.com/ShaoZeMing/capistrano3-doc/blob/master/img/zan002.png
  [3]: https://github.com/ShaoZeMing/capistrano3-doc/blob/master/img/zan004.jpg
  [4]: http://capistranorb.com/documentation/getting-started/installation/
  [5]: https://github.com/ShaoZeMing/capistrano3-doc/blob/master/img/zan003.jpg
