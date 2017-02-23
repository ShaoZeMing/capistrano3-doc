Capistrano是一种通过ssh向多个服务器部署web应用的一种框架和工具。具体更详细的介绍，大家可以登录官方网站或其它相关网站进行了解。

# 软件版本

## 先决条件

1. 操作系统：linux

2. Ruby：2.*（官方要求Capistrano3.* 基于Ruby>2.0即可）

3. Rubygem：2.*

4. capistrano：3.7.2（当前最新版本）

# 安装
- 由于linux系统发行版不同，安装Ruby有一点异常（特别是Capistrano 3 要求必须ruby>2.0以上），特此对Ubuntu和CentOS单独说明安装Ruby和rubygems方法

## Ubuntu 下安装ruby 和 Rubygem

运行一条命令即可：

`sudo apt-get update`
`sudo apt-get install ruby-full rubygems `

![zan001.jpg][1]

由于我安装过了，提示我已近安装了当前Ubuntu最稳定的ruby2.3版本，满足ruby>2.0要求


## CentOS 下安装ruby

### 注：由于CentOS yum库下的ruby版本太低（如下图），无法满足Capistrano 3运行要求，为此只能编译安装>2.0的ruby版本。
![zan002.png][2]

> 1. 下载 `wget https://cache.ruby-lang.org/pub/ruby/2.4/ruby-2.4.0.tar.gz`(若没有wget,请先安装wget：
> `yum install -y wget`)
> 2. 解压 `tar xf ruby-2.4.0.tar.gz`
> 3. 安装编译依赖 `yum install -y gcc-c++ zlib zlib-devel openssl-devel`
> 4. 安装ruby `./configure && make && make install`	#编译时间稍微有点长

## CentOS 下安装rubygems


> 1. 下载 `wget https://rubygems.org/rubygems/rubygems-2.6.10.tgz`
> 2. 解压 `tar xf rubygems-2.6.10.tgz`
> 3. 安装 `cd rubygems-2.6.10`, `ruby setup.rb`


# 安装capistrano

### 方法1：
执行命令：
`gem install capistrano`

![zan002.jpg][3]

由于我安装过了，提示我已近安装了capistrano-3.7.2，这也是当前最新版本了。

### 方法2：
执行命令：

> `git clone https://github.com/capistrano/capistrano.git` 
> `cd capistrano`
> `gem build *.gemspec` 
> `gem install *.gem`

更多安装方法请参考[Captrisano官网][4]

# 查看安装情况

- `ruby -v`;
- `gem -v`;
- `cap -v`

![zan003.jpg][5]

# 总结

capistrano依赖zlib和openssl，安装ruby前需要将这两个软件包安装好，这样安装过程才会比较顺利。

  [1]: http://blog.4d4k.com/usr/uploads/2017/02/1374100548.jpg
  [2]: http://blog.4d4k.com/usr/uploads/2017/02/2471742994.png
  [3]: http://blog.4d4k.com/usr/uploads/2017/02/2134425200.jpg
  [4]: http://capistranorb.com/documentation/getting-started/installation/
  [5]: http://blog.4d4k.com/usr/uploads/2017/02/3324363127.jpg