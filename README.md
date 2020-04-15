# 和我一步步部署 kubernetes 集群

![dashboard-home](./images/dashboard-home.png)

This series of documents describes all the steps for deploying kubernetes v1.16.6 clusters using binary (Hard-Way mode).

During the deployment process, the startup parameters of each component, their meaning and possible problems will be detailed.

Once deployed, you will understand how the components of the system interact with each other so that you can quickly solve real problems.

So this document is mainly suitable for those who have some kubernetes foundation and want to learn and understand the system configuration, operating principles through a step-by-step deployment approach.

This series of documents is for Debian 10 and above and will be updated as each component is updated.

With strict security mechanisms such as x509 certificate bidirectional authentication, RBAC authorization, etc. enabled, it is recommended to deploy from scratch, otherwise authentication, authorization, etc. may fail!

Starting with v1.16.x, the following adjustments have been made to this document.

    Container runtime: replace docker with containerd for simpler, more robust; the corresponding command line tool is crictl.
    Pod network: replacing flannels with calico to enable pod interoperability and support larger clusters.

New indicator monitoring system: cluster indicator collection and monitoring using the mainstream Prometheus, Grafana technology stack.

If you want to continue using the docker and flannel, please refer to the attached documentation.

+ [v1.6.2](https://github.com/opsnull/follow-me-install-kubernetes-cluster/tree/v1.6.2)：已停止更新；
+ [v1.8.x](https://github.com/opsnull/follow-me-install-kubernetes-cluster/tree/v1.8.x)：已停止更新；
+ [v1.10.x](https://github.com/opsnull/follow-me-install-kubernetes-cluster/tree/v1.10.x)：已停止更新；
+ [v1.12.x](https://github.com/opsnull/follow-me-install-kubernetes-cluster/tree/v1.12.x)：已停止更新；
+ [v1.14.x](https://github.com/opsnull/follow-me-install-kubernetes-cluster/tree/v1.14.x)：继续更新；

## 步骤列表

1. [00.组件版本和配置策略](00.组件版本和配置策略.md)
1. [01.初始化系统和全局变量](01.初始化系统和全局变量.md)
1. [02.创建CA根证书和秘钥](02.创建CA根证书和秘钥.md)			
1. [03.部署kubectl命令行工具](03.kubectl.md)			
1. [04.部署etcd集群](04.etcd集群.md)				
1. [05-1.部署master节点.md](05-1.master节点.md)
    1. [05-2.apiserver集群](05-2.apiserver集群.md)
    1. [05-3.controller-manager集群](05-3.controller-manager集群.md)	
    1. [05-4.scheduler集群](05-4.scheduler集群.md)
1. [06-1.部署woker节点](06-1.worker节点.md)			
    1. [06-2.apiserver高可用之nginx代理](06-2.apiserver高可用.md)
    1. [06-3.containerd](06-3.containerd.md)					
    1. [06-4.kubelet](06-4.kubelet.md)				
    1. [06-5.kube-proxy](06-5.kube-proxy.md)
    1. [06-6.部署calico网络](06-6.calico.md)	
1. [07.验证集群功能](07.验证集群功能.md)			
1. [08-1.部署集群插件](08-1.部署集群插件.md)
    1. [08-2.coredns插件](08-2.coredns插件.md)
    1. [08-3.dashboard插件](08-3.dashboard插件.md)
    1. [08-4.kube-prometheus插件](08-4.kube-prometheus插件.md)
	1. [08-5.EFK插件](08-5.EFK插件.md)			
1. [09.部署Docker-Registry](09.Registry.md)	
1. [10.清理集群](10.清理集群.md)	
1. [A.浏览器访问apiserver安全端口](A.浏览器访问kube-apiserver安全端口.md)
1. [B.校验TLS证书](B.校验TLS证书.md)
1. [C.部署metrics-server插件](C.metrics-server插件.md)
1. [D.部署Harbor-Registry](D.部署Harbor-Registry.md)	

## 在线阅读

+ 建议：[GitBook](https://k8s-install.opsnull.com/)
+ [Github](https://www.gitbook.com/book/opsnull/follow-me-install-kubernetes-cluster)

## 电子书

+ pdf 格式 [下载](https://www.gitbook.com/download/pdf/book/opsnull/follow-me-install-kubernetes-cluster)
+ epub 格式 [下载](https://www.gitbook.com/download/epub/book/opsnull/follow-me-install-kubernetes-cluster)

## 打赏

如果你觉得这份文档对你有帮助，请微信扫描下方的二维码进行捐赠，加油后的 opsnull 将会和你分享更多的原创教程，谢谢！

<p align="center">
  <img src="https://github.com/opsnull/follow-me-install-kubernetes-cluster/blob/master/images/weixin_qr.jpg?raw=true" alt="weixin_qr.jpg"/>
</p>

## 广告位

## 版权

Copyright 2017-2020 zhangjun (geekard@qq.com)

知识共享 署名-非商业性使用-相同方式共享 4.0（CC BY-NC-SA 4.0），详情见 [LICENSE](LICENSE) 文件。
