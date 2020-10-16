# openstack学习笔记

## 学习进度

- [x] `openstack`总述（概念、语言、支持环境等）
- [x] `openstack insatallation in ubuntu`（版本、支持的service等）

## 总述

+ **OpenStack**是[美国国家航空航天局](https://zh.wikipedia.org/wiki/美國太空總署)和[Rackspace](https://zh.wikipedia.org/wiki/Rackspace)合作研发的[云计算](https://zh.wikipedia.org/wiki/雲端運算)软件，以[Apache授权条款](https://zh.wikipedia.org/wiki/Apache授權條款)授权，并且是[自由](https://zh.wikipedia.org/wiki/自由軟件)和[开放源代码软件](https://zh.wikipedia.org/wiki/开放源代码软件)。
  
  + **云计算**（英语：cloud computing[[1\]](https://zh.wikipedia.org/wiki/雲端運算#cite_note-杨正洪周发武2011-1)），也被意译为**网络计算**[[2\]](https://zh.wikipedia.org/wiki/雲端運算#cite_note-2)，是一种基于[互联网](https://zh.wikipedia.org/wiki/互联网)的计算方式，通过这种方式，共享的软硬件资源和信息可以按需求提供给计算机各种终端和其他设备，使用服务商提供的电脑基建作计算和资源。
  
+ 以[Python](https://zh.wikipedia.org/wiki/Python)[编程语言](https://zh.wikipedia.org/wiki/程式語言)编写

+ 集成[Tornado](https://zh.wikipedia.org/wiki/Tornado)[网页服务器](https://zh.wikipedia.org/wiki/網頁伺服器)、[Nebula运算平台](https://zh.wikipedia.org/w/index.php?title=Nebula_(運算平台)&action=edit&redlink=1)

+ 使用Twisted软件[框架](https://zh.wikipedia.org/wiki/框架)
  
  + **Twisted** 是一个[事件驱动](https://zh.wikipedia.org/wiki/事件驅動)的[网络编程](https://zh.wikipedia.org/w/index.php?title=网络编程&action=edit&redlink=1)[框架](https://zh.wikipedia.org/wiki/软件框架)，它使用[编程语言](https://zh.wikipedia.org/wiki/编程语言)[Python](https://zh.wikipedia.org/wiki/Python)编写，并在[MIT协议](https://zh.wikipedia.org/wiki/MIT_License)下开源。
  
+ 遵循Open Virtualization Format、AMQP、[SQLAlchemy](https://zh.wikipedia.org/wiki/SQLAlchemy)等标准

+ [虚拟机](https://zh.wikipedia.org/wiki/虛擬機器)软件支持包括：[KVM](https://zh.wikipedia.org/wiki/Kernel-based_Virtual_Machine)、[Xen](https://zh.wikipedia.org/wiki/Xen)、[VirtualBox](https://zh.wikipedia.org/wiki/VirtualBox)、[VMware](https://zh.wikipedia.org/wiki/VMware)、Hyper-V

+ Openstack控制着大型的计算，存储和网络资源池，所有这些都通过API或仪表板进行管理。

  ![](./image/overview-diagram-new.svg)



## installation in ubuntu

+ OpenStack的稳5261定版4102一般需要倒推一个版本1653，4月上线的mitaka版本，所以目前稳定版就是liberty。所以接下来学习`liberty`的指南

+ OpenStack系统由几个关键服务组成，它们可以单独安装。这些服务根据你的云需求工作在一起。这些服务包括计算服务、认证服务、网络服务、镜像服务、块存储服务、对象存储服务、计量服务、编排服务和数据库服务。您可以独立安装这些服务、独自配置它们或者连接成一个整体。

+ **OpenStack services**

  | 服务                                                         | 项目名称                                                     | 描述                                                         |
  | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
  | [Dashboard](http://www.openstack.org/software/releases/liberty/components/horizon) | [Horizon](http://docs.openstack.org/developer/horizon/)      | 提供了一个基于web的自服务门户，与OpenStack底层服务交互，诸如启动一个实例，分配IP地址以及配置访问控制。 |
  | [Compute](http://www.openstack.org/software/releases/liberty/components/nova) | [Nova](http://docs.openstack.org/developer/nova/)            | 在OpenStack环境中计算实例的生命周期管理。按需响应包括生成、调度、回收虚拟机等操作。 |
  | [Networking](http://www.openstack.org/software/releases/liberty/components/neutron) | [Neutron](http://docs.openstack.org/developer/neutron/)      | 确保为其它OpenStack服务提供网络连接即服务，比如OpenStack计算。为用户提供API定义网络和使用。基于插件的架构其支持众多的网络提供商和技术。 |
  | 存储                                                         |                                                              |                                                              |
  | [Object Storage](http://www.openstack.org/software/releases/liberty/components/swift) | [Swift](http://docs.openstack.org/developer/swift/)          | 通过一个 [*RESTful*](https://docs.openstack.org/mitaka/zh_CN/install-guide-ubuntu/common/glossary.html#term-restful),基于HTTP的应用程序接口存储和任意检索的非结构化数据对象。它拥有高容错机制，基于数据复制和可扩展架构。它的实现并像是一个文件服务器需要挂载目录。在此种方式下，它写入对象和文件到多个硬盘中，以确保数据是在集群内跨服务器的多份复制。 |
  | [Block Storage](http://www.openstack.org/software/releases/liberty/components/cinder) | [Cinder](http://docs.openstack.org/developer/cinder/)        | 为运行实例而提供的持久性块存储。它的可插拔驱动架构的功能有助于创建和管理块存储设备。 |
  | 共享服务                                                     |                                                              |                                                              |
  | [Identity service](http://www.openstack.org/software/releases/liberty/components/keystone) | [Keystone](http://docs.openstack.org/developer/keystone/)    | 为其他OpenStack服务提供认证和授权服务，为所有的OpenStack服务提供一个端点目录。 |
  | [Image service](http://www.openstack.org/software/releases/liberty/components/glance) | Glance服务请参见<http://docs.openstack.org/developer/glance/> | 存储和检索虚拟机磁盘镜像，OpenStack计算会在实例部署时使用此服务。 |
  | Telemetry服务请参见<http://www.openstack.org/software/releases/liberty/components/ceilometer> | Ceilometer服务请参见<http://docs.openstack.org/developer/ceilometer/> | 为OpenStack云的计费、基准、扩展性以及统计等目的提供监测和计量。 |
  | 高层次服务                                                   |                                                              |                                                              |
  | Orchestration服务请参见<http://www.openstack.org/software/releases/liberty/components/heat> | Heat服务请参见<http://docs.openstack.org/developer/heat/>    | Orchestration服务支持多样化的综合的云应用，通过调用OpenStack-native REST API和CloudFormation-compatible Query API，支持:term:[`](https://docs.openstack.org/mitaka/zh_CN/install-guide-ubuntu/overview.html#id1)HOT <Heat Orchestration Template (HOT)>`格式模板或者AWS CloudFormation格式模板 |

  在你对基础安装，配置，操作和故障诊断熟悉之后，你应该考虑按照以下步骤使用生产架构来进行部署

  - 确定并补充必要的核心和可选服务，以满足性能和冗余要求。
  - 使用诸如防火墙，加密和服务策略的方式来加强安全。
  - 使用自动化部署工具，例如Ansible, Chef, Puppet, or Salt来自动化部署，管理生产环境









## 参考资料

+ [openstack wiki](https://zh.wikipedia.org/wiki/OpenStack)
+ [twisted wiki](https://zh.wikipedia.org/wiki/Twisted)
+ [openstack](https://www.openstack.org/)
+ [openstack部署实践](https://gtcsq.readthedocs.io/en/latest/openstack/deploy_synopsis.html)
+ [openstack installation in ubuntu](https://docs.openstack.org/mitaka/zh_CN/install-guide-ubuntu/)