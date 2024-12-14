# 分布式存储磁带归档

## 磁带介绍
磁带是一项悠久的IT技术，自IBM 1952年发明磁带技术以来，磁带技术经过多次技术创新。目前主流的磁带技术是LTO联盟的LTO9磁带，以及IBM的TS1170 JF磁带，LTO9磁带可以提供18T非压缩容量，TS1170 JF可以提供惊人的50TB的容量。目前磁带产业联盟已经实现了580TB的技术原型。 

![arc](./580T.png)

磁带存储广泛的应用在数据备份和数据存储领域，尤其是一些重要的数据需要离线备份、空气隔离，保障数据的安全。 
总的来说磁带存储具有如下的优势：
- ** 数据离线保存，抵御黑客攻击
- ** 数据存储成本低
- ** 低功耗、绿色数据存储
- ** 数据容易移动等

磁带介质需要结合带库设备一起使用，根据客户的容量和性能需求，这些设备分入门级的带库存储、中端带库设备和高端带库设备。 入门级的带库存储一般一个驱动器和数盘磁带；中端带库一般十几个驱动器和一两千盘磁带；高端带库有上百个驱动器和几万盘磁带，如IBM的TS4500、昆腾的i6000、Spectra Logic的Spectra TFinity Series。

![arc](./spectra.png)

## 分布式存储集成


## 磁带归档架构
T4C是一个功能强大的磁带归档引擎，整个引擎由缓存文件系统、归档内核、归档外部Rest API接口，以及分布式系统的统一运维监控平台，和数据流转作业调度引擎组成。 

T4C拥有开发的接口，可以无缝对接基于POSIX的分布式存储系统，比如HDFS、CubeFS、Noobaa等。通过与T4C集成，可以实现HDFS等分布式存储的磁带归档功能，降低了整个CubeFS集群的存储成本、优化了企业存储的能耗。 分布式存储通过归档节点的缓存文件系统，实现数据流的对接，简化分布式存储使用磁带存储的过程。 T4C归档引擎在后端通过磁带介质的调度，加载磁带到带机中去，最后把数据复制到磁带介质上，同时记录元数据信息。 T4C通过操作系统的fuse功能来监控分布式存储对数据的访问，如果数据在磁带上，T4C自动加载磁带，复制回数据到磁盘上。

T4C也提供丰富的Rest API接口，CubeFS等集成软件可以调用迁移召回API实现高效的数据落带召回操作；CubeFS也可以通过RestAPI来调用带库设备接口，监控带库设备加载卸载磁带的操作。 

![arc](./t4c.png)

## T4C 团队介绍
T4C团队来自IBM中国开发实验室，团队成员拥有二十年的系统开发经验、磁带归档系统架构规划和落地经验，参与过国内外多个超大规模磁带存储系统的开发交付。
微信联系方式：Tape4Cloud
