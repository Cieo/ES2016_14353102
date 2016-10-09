##Lab1 安装DOL

###Environment
Ubuntu Server 14.04



###Description

#####Distributed Operation Layer : 
>The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.
>[了解更多](www.tik.ee.ethz.ch/~shapes/dol.html)



###How to install

#####0. 安装基础环境
```shell
sudo apt-get update
sudo apt-get install ant
sudo apt-get install openjdk-7-jdk
sudo apt-get install unzip
```
#####1. 下载文件
```shell
sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
```
#####2. 解压文件&编译`systemc`
```shell
#新建dol的文件夹 
sudo mkdir dol

#将dolethz.zip解压到 dol文件夹中
sudo unzip dol_ethz.zip -d dol

#解压systemc
sudo tar -zxvf systemc-2.3.1.tgz

#解压后进入systemc-2.3.1的目录下
cd systemc-2.3.1

#新建一个临时文件夹objdir
sudo mkdir objdir

#进入该文件夹objdir
cd objdir

#运行configure(能根据系统的环境设置一下参数，用于编译)
sudo ../configure CXX=g++ --disable-async-updates

#编译
sudo make install

#记录当前工作路径
cd ..
ls
sudo pwd
```

#####3. 编译dol
```shell
#进入刚刚dol的文件夹
cd ../dol

#修改build_zip.xml文件
#找到下面这段话，就是说上面编译的systemc位置在哪里，
<property name="systemc.inc" value="XXX/include"/>
<property name="systemc.lib" value="XXX/lib64-linux/libsystemc.a"/>
#把XXX改成上页pwd的结果

#编译
sudo ant -f build_zip.xml all
#成功会显示build successful

#运行第一个例子
cd build/bin/main
ant -f runexample.xml -Dnumber=1
```



###Experimental experience
TA的实验文档给的很详细，只要跟着文档做，即可配置成功。如果出现错误的话可以切换英文系统再次尝试。