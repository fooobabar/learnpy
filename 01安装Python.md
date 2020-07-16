[toc]
# Python开发环境安装

## 安装vagrant

## 安装Python

### 安装编译Python需要的系统包
```bash
# cd /etc/yum.repos.d
# mkdir bak
# mv *.repo bak
# wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
# yum clean all 
# yum -y install openssl-devel readline readline-devel zlib zlib-devel sqllite sqlite-devel

```

### 编译Python3.6.11
```bash
[root@devops ~]# cd /vagrant
[root@devops vagrant]# ls
Python-3.6.11.tgz  Vagrantfile

[root@devops vagrant]# tar -xf Python-3.6.11.tgz -C /tmp
[root@devops yum.repos.d]# cd /tmp/Python-3.6.11/
[root@devops Python-3.6.11]# ./configure --prefix=/usr/local/python36  && make && make install
省略输出
...
[root@devops Python-3.6.11]# cd /usr/local/python36

```

### 调整pip指向豆瓣源
```bash
# cat <<  EOF >/etc/pip.conf
> [global]
> timeout = 60
> index-url = http://pypi.douban.com/simple
> trusted-host = pypi.douban.com
> EOF
```

### 调整环境变量
__/etc/profile.d/目录下新增呢个python3.sh，在其中声明变量__
```bash
[root@devops lession04]# cd /etc/profile.d
[root@devops profile.d]# ls
256term.csh    colorgrep.sh  lang.csh  less.sh           python3.sh
256term.sh     colorls.csh   lang.sh   puppet-agent.csh  which2.csh
colorgrep.csh  colorls.sh    less.csh  puppet-agent.sh   which2.sh
[root@devops profile.d]# cat python3.sh 
export PATH=/usr/local/python3/bin:$PATH
```

### 安装ipython
ipython交互性比较好，每次新装Python都会带上ipython

```bash
[root@devops ~]# pip3 install ipython

```

### 升级pip
```bash
# pip3 install --upgrade pip
```